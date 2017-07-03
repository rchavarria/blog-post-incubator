# Setting up Jenkins

[Getting started with Pipelines](https://jenkins.io/doc/pipeline/)

Jenkins is like CRON, but on steroids

It's awesome to automate things, mundane things, boring things

Download a `.war` file from the downloads page. Place it in a directory of your choice and run

    java -jar jenkins.war

Export JAVA_HOME env variable:

    export JAVA_HOME=/usr/lib/jvm/default-java

You should have `java` (version 1.7 or greater) installed and running.

The first time, it'll give you a first administrator password. When you visit http://localhost:8080/ it will ask you for that password. After entering the password, you'll be asked to install some plugins.

Everything is installed in `~/.jenkins` folder. No database. If you delete this folder, you'll start from scratch.

Then, you need to create the admin account.

Go to Manage Jenkins > Configure Global Security to configure authorization and authentication

Go to Manage Jenkins > Manage Users to add/remove users

## Docker

That's a very convenient way of running Jenkins. There is a hub in http://hub.docker.com with Jenkins images and there is documentation too about how to install and how to run Jenkins in a docker container.

# Creating application builds

Clone the repo https://github.com/g0t4/jenkins2-course-spring-boot.git

Go to `spring-boot/spring-boot-samples/spring-boot-samples-atmosphere`. You'll build that project with Maven

Install Maven

`mvn compile` to compile the Java code

`mvn test` to run tests

`mvn test` to run tests

`mvn package` to package your app in a `.war` o `.jar` file

In the project configuration, go to *Source code management*, and enter the URL for the repo

Then, go to *Build* and add a build step, *Maven targets*, especifying `compile` as maven target and `spring-boot-samples/spring-boot-sample-atmosphere/pom.xml` the target POM file

*Project view*: the page where options about the project or job are shown

*Build view*: the page where you can see optoins for a specific build

*Console view*: to see what commands are executed

*Workspace*: source code of our project. `JENKINS_HOME/jobs/<job name>/workspace`

From the Project view, you can navigate the project's workspace

The workspace is common for the project, so files may be modified from build to build

A way to keep interesting files (for example, a `.jar` file with our app) we need to configure a *Post-Build step* to *Archive artifacts*

The archived artifact will be shown in the Project view in this case. It depends on what type of artifact and what plugin do you use

**What's the difference between a Job and a Build?** A Job is defined by a configuration file. A Job can be seen as a step in the build process of our application. A Job can have multiple Builds associated with it. A Build is the result of executing a Job.

# Testing and CI

Add build steps to your project: execute shell script, run maven target,...

Add build triggers or build post-build actions

But that way is the *old* way. We're going to take a look at the modern way, the Pipeline way.

When creating a Pipeline project, there is no *build* step, or *post-build* actions step. Instead, there are advanced options and *pipeline* steps.

Pipelines are described in Groovy scripts.

In Pipelines, there is a command, `step`, that includes all standard steps for Free Style projects.

```
node {
    git branch: '*/master', url: 'https://github.com/g0t4/jenkins2-course-spring-boot.git'
    
    def projectPath = 'spring-boot-samples/spring-boot-sample-atmosphere'
    dir(projectPath) {   // run commands in a custom workind directory
        sh 'mvn clean package' // run shel command
    
        archiveArtifacts 'target/*.jar'  // archive .jar files
    }
}
```

"Master Agent model" sub-chapter is really interesting.

Something interesting about pipelines are *Stage view*. You can add a stage to the Pipeline script with:

```
stage 'Stage name'
...
```

Absolutely fantastic! In the project view, you can see a graph/table/visual-thing about what stages have been successful, what ones have failed, how much time they took to run,... Impresive!

Email notification in a Pipeline

Choose step `emailext`

One can define functions in Pipeline scripts. Awesome! You can define a `notify` method:

```
def notify(status) {
  emailext(
    to: 'rchavarria@whatever.com',
    subject: "Job ${env.JOB_NAME}",
    body: "${status}"
  )
}
```

Notify on errors

As the pipeline script is just a groovy script, we can use `try-catch` blocks. Hmmm, this sound weird to me, but ok.

Visualizing test results: through the traditional step of "Publish JUnit..."

# Finding and managing plugins

Integrating code coverage 

For a java project managed with Maven, just run `mvn verify` to generate a HTML code coverage report at `target/site`.

Publishing HTML reports

Pipeline command:

```
ublishHTML(target: [
            allowMissing: true,
            alwaysLinkToLastBuild: false,
            keepAll: true,
            reportDir: 'target/site/jacoco/',
            reportFiles: 'index.html',
            reportName: 'Code Coverage',
            reportTitles: ''
        ])
``Pipeline command:

```
publishHTML(target: [
            allowMissing: true,
            alwaysLinkToLastBuild: false,
            keepAll: true,
            reportDir: 'target/site/jacoco/',
            reportFiles: 'index.html',
            reportName: 'Code Coverage',
            reportTitles: ''
        ])
````

BlueOcean UI plugin

A new user interface for Jenkins

It's a experimental plugin for now. You need to go to `Advanced` tab in the `Manage plugins` and add a new source for plugins.

# Building continuous delivery pipelines

## Backup and restore

Just gzip and copy Jenkins home directory. Then, paste it whenever you want, ungzip it and you'll go:

```
tar -czf jenkins-home.tar.gz ~/.jenkins
tar -xzf jenkins-home.tar.gz <another/path>
```

## Stashing pipelines

There is a pipeline command, `stash` to save a *copy* of some files to reuse them in the rest of the pipeline. *stash* means: *reserva oculta*. It's like archiving, but it only lasts the duration of the pipeline.

## Browsing workspace in Pipelines

Workspaces live inside nodes. Every pipeline must reserve a node. To go to the workspace: go to *Pipeline steps*, select the step *Node* and you'll see the workspace.

## Allocating a second node

Each time we allocate a node, we're not sure we have the same workspace in all different nodes. Usually, it's the same, but it's not guaranteed.

To share the workspace, we use the `stash` phase/step.

To get a shared workspace (a *stashed* one), we can `unstash <stash-name>`.

Create a new Node in Jenkins, a new Agent:

- Name
- # of executors
- Remote root dir: it can be `/tmp/jenkins-<agent-name>`
- Labels: to identify this agent in Pipelines
- Launch method: launch agent via Java Web Start can be a good option

When allocating a node in a Pipeline, with `node`, you can pass some parameters, for example, one label we gave the Agent before: `node('agent1_label')`

## Execution and Monitoring parallel builds

The following code will run tests in **parallel**, each one will allocate a new node:

```
// create a new stage
stage 'Browser testing'

// run different tests in parallel
parallel chrome: {
  runTests('Chrome')
}, firefox: {
  runTests('Firefox')
}, phantomjs: {
  runTests('PhantomJS')
}

def runTests(browser) {
  // each run will allocate a new node
  node {
    sh 'rm -rf *'
    unstash 'everything'
    // run tests
    sh "npm run test-single-run -- --browsers ${browser}"
    // archive test results
    step([$class: 'JUnitResultArchiver', testResults: 'test-results/**/test-results.xml'])
  }
}
```

## Manual approval step

`input` step is a way to ask the user to enter some data by hand, so it can work as a manual approval, a human must say "Yes" to continue the execution of the job

Do not use `input` inside a `node` step. It will pause an executor until a human press a button. A common pattern to use with `input` is the following:

```
// first, notify (it must be done in a node)
node {
  call_my_notify_method('You must click to continue')
}

// outside any `node`
input 'Is it ready to continue?'
```

There are heavyweight executors and lightweight executors. heavyweight ones run code inside a `node` step, they're common executors. lightweight ones run Pipeline code outside `node`, but they can't run `sh` steps or are not designed to do that.

Lightweight executors belong only to *master* node.

## Deploy to staging

```
// concurrency `1` means we only want 1 of these stages to be run at the same time, only the newest will be run. the rest will be cancelled by Jenkins
stage 'Deploy', concurrency: 1
```

Well, now, it seems `stage` needs a block syntax `{}` and it doesn't accept a parameter called `concurrency`, there will be a new way to accoplish that.

## Jenkinsfile

You can get the content of the Pipeline and make it part of the project source code.

# Summary

Advantages:

1. Split jobs into different stages
2. It saves the work if Jenkins crash, then it starts when it was
3. Manual verification

Resources:

- jenkins.io/doc

