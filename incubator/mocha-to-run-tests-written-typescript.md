# typescript-mocha

Project to check if mocha tests can be written in TypeScript

# How to

## Requirements 

- NodeJS

## Steps 

Configure `npm` to handle dependencies

    npm init

Install [TypeScript]. First, try no to install globally, just for testing

    npm install --save typescript

Check TypeScript installation

    node_modules/.bin/tsc --version

Install [TSD]

    npm install --save tsd

Check TSD installation

    node_modules/.bin/tsd --version

Install [mocha] and [chai]. I have a more detail post about [How to set up a NodeJS project with mocha, chai and sinon]

    npm install --save-dev mocha chai

Install mocha and chai TypeScript definition files, with TSD

    node_modules/.bin/tsd query mocha --save --action install
    node_modules/.bin/tsd query chai --save --action install

Create a test, written in TypeScript

    mkdir test
    vi test/test.ts

Write some tests in it, for example :

    /// <reference path="../typings/mocha/mocha.d.ts" />
    /// <reference path="../typings/chai/chai.d.ts" />
    import chai = require('chai');
    var expect = chai.expect;

    describe('Unit Tests:', () => {
        describe('2 + 4', () => {
            it('should be 6', (done) => {
                expect(2+4).to.equals(6);
                done();
            });
        });
    });

Compile TypeScript file to JavaScript

    node_modules/.bin/tsc --module commonjs test/test.ts

Run tests with mocha

    node_modules/.bin/mocha

You should see the results :

    Unit Tests:
        2 + 4
            √ should be 6

    1 passing (13ms)

# References

- [Testing with mocha, chai and TypeScript]

# TODOs

- Introduce `gulp`
- Configure `gulp` to run `mocha`
- Configure `gulp` to compile TypeScript and then run `mocha`

[Testing with mocha, chai and TypeScript]: http://dinozafirakos.com/2014/07/21/testing-with-mocha-chai-and-typescript

