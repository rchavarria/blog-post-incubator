# Aprendiendo Ionic 2

Recientemente se ha celebrado la conferencia [Angular Connect] en Londres, donde se ha hablado mucho de [Angular 2], framework de desarrollo de aplicaciones web en el que estoy muy interesado (de hecho estoy desarrollando una pequeña aplicación para diversión de mi hijo, [English by Einar]). También estoy enteresado en el framework [Ionic], que aúna los proyectos de Angular y [Cordova] y que permite desarrollar aplicaciones para móviles con herramientas de desarrollo web: HTML5, CSS3 y JavaScript.

En dicha conferencia se hizo público la versión alpha de [Ionic 2], la versión de Ionic que incluye la nueva versión de Angular. Ionic es un *BLA BLA BLA BLA* y su versión 2 siguen con la filosofía de estar muy preocupados con el rendimiento. En este post veremos lo realmente fácil que es comenzar a desarrollar con estas herrmientas.

## Requisitos

Ionic se apoya en Cordova y en las plataformas de desarrollo nativas dependiendo de la plataforma móvil en la que estemos enfocados, normalmente Android o iOS. Antes de comenzar a desarrollar con él deberemos actualizar a las versiones más modernas posibles, ya que la versión alpha de Ionic 2 requiere de los últimos avances.

En mi caso particular, he necesitado actualizar mi SDK de Android para Linux:

``` bash
rchavarria@home$ ./AndroidSDK/tools/android sdk
```

para abrir la interfaz gráfica y poder actualizar algunos paquetes del SDK.

Y también he necesitado actualizar las versiones de NodeJS (a través de `nvm`, Node Version Manager), la herramienta `npm` y Cordova:

``` bash
rchavarria@home$ nvm install v5.0.0
rchavarria@home$ npm install -g npm
rchavarria@home$ npm install -g cordova@5.3.3
```

Por último, instalar la versión alpha de Ionic 2. No temas, no hay peligro de romper proyectos desarrollados con la versión 1 de Ionic.

``` bash
rchavarria@home$ npm install -g ionic@alpha
```

## Creación del primer proyecto

Para mi primer proyecto he usado una plantilla desarrollada por la gente de Ionic, [tutorial]. Estas plantillas permiten tener una aplicación muy básica funcionando en unos minutos. Esta plantilla contiene un menú deslizante lateral, pero hay otras muchas plantillas. Crear el proyecto es un simple comando:

``` bash
rchavarria@home$ ionic start MyFirstIonic2Project tutorial --v2
```

Este comando descarga la plantilla indicada, `tutorial`, instala dependencias de NodeJS y nos deja el proyecto listo para ser ejecutado. De hecho, para poder probarlo en un navegador, basta con escribir los comandos:

``` bash
rchavarria@home$ cd MyFirstIonic2Project
rchavarria@home$ ionic serve
```

## Estructura del proyecto

Prácticamente todos los ficheros de la aplicación están localizados en el directorio `www`, como en todo proyecto de Cordova.

El punto de entrada principal es `www/index.html`. Como página principal, carga los ficheros CSS, incluye los JavaScript y arranca la aplicación. Ionic busca una etiqueta `ion-app` dentro de esta primera página HTML.

Todo el código JavaScript que se encuentra en el directorio `www/app` se transpila a la versión correcta de JavaScript que soporte el navegador para el que está dirigida la aplicación. En este directorio podremos encontrar código tanto TypeScript como ECMAScript 2015. 

En el archivo `www/app/app.js` podemos encontrar la entrada a nuestra aplicación. Crea un component con el decorador `@App`, componente necesario para toda aplicación Ionic.

``` javascript
@App({
  templateUrl: 'app/app.html'
})
class MyApp {
//...
}
```

El código de `@App` configura el archivo `www/app/app.html` como plantilla para la aplicacion. Veámoslo:

``` html
<ion-menu [content]="content">

  <ion-content>
    <ion-list>
      <button ion-item *ng-for="#p of pages" (click)="openPage(p)">
      </button>
    </ion-list>
  </ion-content>

</ion-menu>

<ion-nav id="nav" [root]="rootPage" #content swipe-back-enabled="false"></ion-nav>
```

Esta plantilla define un menu bajo la etiqueta `ion-menu`, y un componente de navegación, `ion-nav`, ambos proporcionados por Ionic. `ion-menu` toma una propiedad para mostrar un contenido, `content`, la cual se la podemos proporcionar a través de la variable `#content` desde nuestro `ion-nav`.

`ion-nav` define un *data binding* a la propiedad `root` del componente, igual que `ion-menu` define un *data binding* a la propiedad `content` (en Angular 2, los *data binding* son unidireccionales por defecto y se declaran mediante corchetes en atributos de las etiquetas HTML). Cuando se cargue el controlador de la navegación, el componente referenciado por la variable `rootPage` será mostrada como la página principal de nuestra aplicación.

En `www/app/app.js`, el componente raiz de la aplicación, `MyApp`, especifica dos propiedades: `pages` y `rootPage`

``` javacript
import {App, IonicApp, IonicPlatform} from 'ionic/ionic';
import {HelloIonicPage} from './hello-ionic/hello-ionic';
import {ListPage} from './list/list';
// ...
class MyApp {
  constructor(app: IonicApp, platform: IonicPlatform) {
    // set up our app
    // ...

    // set our app's pages
    this.pages = [
      { title: 'Hello Ionic', component: HelloIonicPage },
      { title: 'My First List', component: ListPage }
    ];

    // make HelloIonicPage the root page
    this.rootPage = HelloIonicPage;
  }
  // ...
}
```

## Cómo se crea un página

El componente HelloIonicPage se define en el fichero `www/hello-ionic/hello-ionic.js`. Contiene un decorador `@Page`, proporcionado por Ionic, y su nombre lo dice todo. Este componente crea una página Ionic, que consta de un componente y una vista de Angular 2.

``` javascript
import {Page, NavController} from 'ionic/ionic';

@Page({
  templateUrl: 'app/hello-ionic/hello-ionic.html'
})
export class HelloIonicPage {
  constructor(nav: NavController) {
    this.nav = nav;
  }
}
```

Cada página se compone de un componente JavaScript y de una plantilla HTML. Veamos ésta última:

``` html
<ion-navbar *navbar>
  <a menu-toggle><icon menu /></a>
  <ion-title>Hello Ionic</ion-title>
</ion-navbar>

<ion-content>
  <h3>Welcome to your first Ionic app!</h3>
  <p>
    ...
  </p>
</ion-content>
```

La etiqueta `<ion-navbar *navbar>` funciona como configuración para la barra de navegación. Es quien incluye los botones a mostrar en dicha barra, así como el título.

## Navegando entre páginas

La otra página, `ListPage`, contiene una lista de elementos que el usuario puede tocar (o hacer click) para acceder a ellas. Dicha página está definida en el archivo `www/app/list/list.js`.

``` javascript
import {IonicApp, Page, NavController, NavParams} from 'ionic/ionic';

@Page({
  templateUrl: 'app/list/list.html'
})
export class ListPage {
  constructor(app: IonicApp, nav: NavController, navParams: NavParams) {
    this.nav = nav;
    // ...
   }

   itemTapped(event, item) {
     // ...
   }
}
```

La plantilla de esta página, definida en `www/app/list/list.html`, es quien mostrará una lista de elementos. `*ng-for` es la sintaxis de Angular 2 para reproducir la misma funcionalidad que `ng-repeat` en AngularJS. El manejador del evento click se establece con `(click)=itemTapped(...)` (en Angular 2, se utilizan los paréntesis en atributos de las etiquetas HTML para establecer los manejadores de eventos). De esta forma, cada vez que el usuario toque/haga click en un elemento, el método `itemTapped` será llamado.

``` html
<ion-item *ng-for="#item of items" (click)="itemTapped($event, item)">
```

Para navegar a una nueva página, se puede usar el componente `NavController`, también proporcionado por Ionic. Anteriormente, se ha almacenado una referencia a dicho componente en el atributo `nav` de `ListPage`.

``` javascript
import {ItemDetailsPage} from '../item-details/item-details';
// ...
itemTapped(event, item) {
  this.nav.push(ItemDetailsPage, {
    item: item
  });
}
```

## ¿Y ahora qué?

Ya tenemos una estructura muy básica para el proyecto, y ya sabemos cómo crear páginas y cómo funciona la navegación en Ionic 2. El siguiente paso se me ocurre que podría ser incluir las herramientas y la estrutura necesaria para poder incluir tests en nuestro proyecto. Lo siento si te parece una lata, pero creo que los tests son una herramienta imprescindible en cualquier proyecto, sea de la embergadura que sea. Considero que los tests son básicos para tener un mínimo de calidad en cualquier proyecto software.

## Referencias

- Documentación sobre [componentes de Ionic 2]
- Documentación sobre [el API de dispositivos de Ionic 2]
- [Recursos], en general, de Ionic 2
- [Tests en Angular 2]

[Angular Connect]
[Angular 2]
[English by Einar]
[Ionic]
[Cordova]
[Ionic 2]
[tutorial]
[componentes de Ionic 2]: http://ionicframework.com/docs/v2/components
[el API de dispositivos de Ionic 2]: http://ionicframework.com/docs/v2/platform
[Recursos]: http://ionicframework.com/docs/v2/resources/
[Tests en Angular 2]: https://angular.io/docs/ts/latest/testing/

