---
layout: inner
title: Instagram
lead_text: Crea un clon de Instagram desde cero
permalink: /instagram/
---

<div class="repo">
  <h3>repositorio de la aplicación</h3>
  <a href="https://github.com/railsgirls-cali/instagram-2019</a>
</div>


## RUBY ON RAILS

### ¿Qué es Rails?

Un recordatorio rápido sobre Rails.

Rails es un framework de desarrollo de aplicaciónes web escrito en el lenguaje de programación Ruby. Está diseñado para hacer que la programación de aplicaciónes web sea más fácil, haciendo supuestos sobre lo que cada desarrollador necesita para comenzar. Te permite escribir menos código realizando más que muchos otros lenguajes y frameworks. Además, expertos desarrolladores en Rails reportan que hace que el desarrollo de aplicaciones web sea más divertido.

Rails te permite escribir un buen código evitando que te repitas y favoreciendo la convención antes que la configuración.


### Convención antes que configuración

La convención antes que la configuración es un concepto simple que se utiliza principalmente en la programación. Significa que el entorno en el que trabaja (sistemas, bibliotecas, lenguaje ...) asume muchas situaciones lógicas por defecto, por lo que si te adaptas a ellas en lugar de crear tus propias reglas cada vez, la programación se convierte en una tarea más fácil y productiva.

El objetivo es disminuir el número de decisiones que debes tomar como programador y eliminar la complejidad de tener que configurar todas y cada una de las áreas de desarrollo de aplicaciones. El resultado inmediato es que puedes crear muchas más cosas en menos tiempo.

Los entornos de programación altamente exitosos como Ruby on Rails se basan en este concepto. Si sigue las convenciones establecidas, puede desarrollar una aplicación Rails en mucho menos tiempo y con muchas menos líneas de código de las que necesitaría desarrollar una aplicación web en otros lenguajes.


### MVC (Model, View, Controller)

En le transcurso de este proyecto vamos a hablar de conceptos de arquitectura y programación como vistas o controladores que usa Rails debido a que sigue un patrón de arquitectura que se llama MVC.

El MVC o Modelo-Vista-Controlador es un patrón de arquitectura de software que, utilizando 3 componentes (Vistas, Models y Controladores) separa la lógica de la aplicación de la lógica de la vista en una aplicación.

- **MODELO** Se encarga de los datos consultando la base de datos. Actualizaciones, consultas, búsquedas, etc. todo eso va aquí, en el modelo.

- **CONTROLADOR** Recibe las órdenes del usuario y se encarga de solicitar los datos al modelo y de comunicárselos a la vista.

- **VISTAS** Son la representación visual de los datos, todo lo que tenga que ver con la interfaz gráfica va aquí. Ni el modelo ni el controlador se preocupan de cómo se verán los datos, esa responsabilidad es únicamente de la vista.


## GUIA

La mejor forma de usar esta guía es seguir cada paso tal y como se muestra. No hemos ahorrado ninguna línea de código en las explicaciones, así que puedes seguirla literalmente paso a paso.

Antes de iniciar a programar veremos 2 puntos importantes.


### 1. consola/terminal

La interfaz de línea de comandos, terminal o consola es un método que permite a los usuarios dar instrucciones a algún programa informático por medio de una línea de texto simple.

Lo primero que debemos saber es que el terminal se utiliza para dar órdenes al sistema mediante unas palabras llamadas comandos de Linux. Estos comandos pueden servir para muchas cosas, como por ejemplo: copiar archivos, comprimir carpetas, reproducir música, descargar archivos, etc.

Para que nosotros sepamos que el sistema está preparado para recibir órdenes, en el terminal aparecerá una línea de texto llamada prompt

```
$
```

Entonces cada vez que vas a encontrar referencia a la `consola` en la guía, solo copia el comando y ejecútalo en la consola.


### 2. Modificación de archivos

Encontrarás referencias como la siguiente para ubicar el archivo que tienes que cambiar

**app/views/pages/home.html.erb**

Con instrucciones y el codigo que tienes que agregar o cambiar

```
[...]

codigo

[...]
```

## INICIO

## 1. Crea una aplicación nueva

### ¡Vamos a crear  una nueva aplicación basada en Instagram!

En la consola

```bash
rails new instagram
```

Despues de este comando presiona enter y se va a crear una serie de archivos y dependencias organizados en carpetas que conforman la estructura de una aplicación Rails

Una vez terminado puedes ver la ultima linea que dice:

```
Webpacker successfully installed 🎉 🍰
```

Después de crear la aplicación, entra a su directorio para continuar trabajando directamente en ella:

En la consola

```
cd instagram
```


### El archivo Gemfile

Ahora que creamos este nuevo proyecto con los archivos necesario para iniciar un proyecto de Rails echale una mirada al archivo **Gemfile**.
Este archivo es la base de Rails y donde encontraras las librerias que hacen funcionar nuestra aplicación.
Ademas estaremos agregando nueva librerias en el transcurso de este proyecto para agregar nueva funcionalidades a nuestro proyecto.


## 2. Página de inicio

Una vez que tenemos la primera parte lista podemos ejecutar un nuevo comando en la consola:

```
rails server
```

Eso va a arrancar nuestro servidor de aplicación.

Deberías ver algo parecido a:

```
=> Booting Puma
=> Rails 6.0.0 application starting in development
=> Run `rails server --help` for more startup options
Puma starting in single mode...
* Version 3.12.1 (ruby 2.6.2-p47), codename: Llamas in Pajamas
* Min threads: 5, max threads: 5
* Environment: development
* Listening on tcp://localhost:3000
Use Ctrl-C to stop
```

Que significa que nuestra aplicacion ya esta corriendo en el navegador.

En el navegador, ve a la URL: [http://localhost:3000](http://localhost:3000) . Esta es la página de inicio por defecto para las aplicaciones Rails.

La página "Yay! You’re on Rails!" es la primera prueba para una nueva aplicación Rails. Ésta asegura que tienes el software configurado correctamente para servir una página.


## 3. Crea una primera página

Para crear nuestra primera pagina, necesitas crear como mínimo una ruta, un controlador y una vista.


### Ruta

La ruta define donde se va a encontrar nuestra pagina y quien va a tener responsabilidad de mostrar el contenido.


### Controlador

Esta responsabilidad es la del controlador
El propósito de un controlador es recibir las peticiones (requests) de la aplicación.

A menudo, hay más de una ruta para cada controlador, y diferentes rutas pueden ser servidas por diferentes acciones (actions). El propósito de cada acción es obtener información para pasarla después a la vista.


### Vista

El propósito de una vista es mostrar la información en un formato legible para los humanos. Una distinción importante que hacer es que es el controlador, y no la vista, donde la información es recolectada. La vista sólo debería mostrar la información. Por defecto, las plantillas de las vistas están escritas en un lenguaje llamado ERB (del inglés, Embedded Ruby), que se procesa automáticamente para cada petición servida por Rails.


### Ahora la nueva pagina

Vamos a crear una pagina de `inicio` y iniciamos creando un nuevo controlador.

Para crear un nuevo controlador, necesitas ejecutar el generador de controladores y decirle que quieres un controlador llamado por ejemplo `pages` con una acción llamada `home`. Para ello, ejecuta lo siguiente:

**NOTA** El primer tab de tu consola ya tiene el servidor de Rails corriendo que lanzaste con el comando:

```
rails server
```

Ahora tienes que abrir un nuevo tab.
En la consola aparecerá un nuevo prompt `$ ` donde puedes ejecutar:


`consola`

```
rails generate controller pages home
```

Rails creará una serie de archivos y añadirá una ruta por ti.

```
create  app/controllers/pages_controller.rb
route  get 'pages/home'
invoke  erb
create    app/views/pages
create    app/views/pages/home.html.erb
invoke  test_unit
create    test/controllers/pages_controller_test.rb
invoke  helper
create    app/helpers/pages_helper.rb
invoke    test_unit
invoke  assets
invoke    scss
create      app/assets/stylesheets/pages.scss
```

Estas convenciones que estabamos hablando un poco mas arribas son las que permiten definir lo que se va a crear cada vez que ejecutemos un comando de Rails. Podríamos tambien crear los archivos a mano y escribir el codigo pero Rails se encarga de crear el esqueleto o la estrucutra base para ahorarnos tiempo y implementar buenas practicas basadas en la experiencia colectiva de los desarolladores que contribuyen en proyectos de codigo abiertos como Ruby on Rails.


Los archivos más importantes que acabamos de crear con el generador son por supuesto el controlador, que se encuentra en **app/controllers/pages_controller.rb** y la vista (HTML), que se encuentra en **app/views/pages/home.html.erb**.

Miremos un poco acerca de la convencion que sigue estos archivos.
La mayoría del trabajo en esta guia se llevará a cabo en la carpeta **app/**, y vemos que el primer archivo el controlador se creo en una carpeta que se llama `controllers`, se llama `pages_controller.rb` y tiene una accion llamada `home`.

```ruby
class PagesController < ApplicationController
  def home
  end
end
```

Le coresponde entonces un vista ubicada en el archivo `views` con el nombre `home.html.erb` que va a contener la representacion en codigo HTML de lo que queremos mostrar en el navegador.

Y todo no podría funcionar sin nuestra ruta que tambíen fue añadida con el mismo comando
La puedes ver abriendo el archivo **config/routes.rb**

```ruby
Rails.application.routes.draw do
  get 'pages/home'
  # For details on the DSL available within this file, see https://guides.rubyonrails.org/routing.html
end
```

**NOTA** El algunos archivos puedes ver un texto que impieza con el numeral `#`. Este texto hace parte de los comentarios que se estan autogenerando que dan algunas indicaciones a a el usuarios de como seguir la convenciones de Rails.


### Actualiza el texto en la nueva página

Ahora actualizaremos el archivo de inicio.
Abre el archivo **app/views/pages/home.html.erb** en tu editor de texto y edítalo para que contenga sólo está línea de código:

```html
<h1>¡Bienvenidos a Instagram!</h1>
```

En tu navegador, ve a la URL : [http://localhost:3000/pages/home](http://localhost:3000/pages/home) y ve la nueva página que se acaba de crear.


### Mostrar la página de inicio de tu aplicación (Home)

¿Cómo conectar la raíz de tu sitio a un controlador y acción específica?

Debemos configurar la ruta de acceso a la aplicación editando el archivo **config/routes.rb**, para esto debemos cambiar la siguiente línea en el mismo:

**config/routes.rb**

Reemplazar la línea

```ruby
get 'pages/home'
```

...por:

```ruby
root 'pages#home'
```

Este pequeño cambio indica a Rails que en la pagina de inicio de nuestra aplicación ubicada enla direccion web [http://localhost:3000/](http://localhost:3000/) queremos mostrar la pagina `home`.


## 4. Crea más paginas

### Añade una nueva acción en el controlador

**app/controllers/pages_controller.rb**

```ruby
class PagesController < ApplicationController
  def home
  end

  def about
  end
end
```

Como puedes ver acabamos de agregar debajo de la accion `Home` una nueva accion `about`.
Así tenemos la estructura basica de nuestra aplicación donde tenemos una pagina de inicio y una nueva pagina `about` para contar un poco sobre nosotros.


###  Crea el siguiente archivo:

**app/views/pages/about.html.erb**


#### y agrega lo siguiente:

```html
<h1>¿Quién soy?</h1>
<p>¡Una Rails Girl creando mi propia app de Instagram!</p>
```

###  Vamos a Agregar una nueva ruta

**config/routes.rb**

Debajo de

```ruby
root 'pages#home'

```

Añade:

```ruby
get 'about' => 'pages#about'
```

Ahora en el navegador puedes visitar nuestras dos paginas:

- [http://localhost:3000/](http://localhost:3000/): la pagina de inicio
- [http://localhost:3000/pages/about](http://localhost:3000/pages/about): la pagina donde encontrar información sobre ti en tu proyecto.


## 5. ¡Instalemos Bootstrap!

### Añade Bootstrap con Webpack

Ahora vamos a dedicar un poco de tiempo en configurar toda la parte de Front end de de nuestra aplicación por eso vamos a usar un Framework llamado Bootstrap.

- **Bootstrap** es una biblioteca multiplataforma o conjunto de herramientas de código abierto para diseño de sitios y aplicaciones web. Contiene plantillas de diseño con tipografía, formularios, botones, cuadros, menús de navegación y otros elementos de diseño basado en HTML y CSS, así como extensiones de JavaScript adicionales.
Boostrap facilita la maquetación de sitios web y nos ofrece las herramientas para que nuestro sitio web se vea bien en toda clase de dispositivos, ahorrandonos así el trabajo de tener que rediseñar un sitio web.
Inicialmente creado como una solución interna para twitter y posteriormente liberado al público en agosto del 2011 como un proyecto Open Source en GitHub, en los meses siguientes a su liberación la comunidad apoyó activamente este proyecto hasta convertirlo en lo que es hoy "the most popular HTML, CSS, and JS framework for developing responsive, mobile first projects on the web." como lo indica en su [https://getbootstrap.com/](página web).

Existe varias manera de integrarar Bootstrap con la parte de Frontend de Rails, es decir todo el codigo Javascript y CSS que se usa en la parte de la vista y que permite renderizar aplicaciones dinamicas en el navegador.
En nuestro ejemplo vamos a ver una de la mas popular que se llama `Webpack`.

- **Webpack** es un Module Bundler for modern JavaScript applications, es decir, un empaquetador de módulos para aplicaciones modernas hechas en JavaScript.

Una aplicación web lleva múltiples tipos de assets como imágenes, fuentes personalizadas, JSON, CSS, JavaScript, etc. y manejar esto se vuelve un dolor de cabeza a medida que nuestra aplicación tiene éxito y va creciendo. Todo esto lo resuelve Webpack y es por eso que será nuestro empaquetador de módulos (o Module Mundler).

Tener una aplicación organizada va a ayudarte a llevar un correcto manejo de versiones de tu código. También necesitarás organizar carpetas llenas de archivos en toda clase de extensiones y separar las que se usan en entornos de desarrollo, como las que se usarán en producción. Esto lo hace Webpack de manera fácil, solo debes decirle dónde está el archivo fuente y a dónde quieres enviar el o los archivos resultantes.


### Paso a paso

El primero comando que vamos a utlizar es

`consola`

```
yarn add bootstrap jquery popper.js
```

Acabamos de instalar los paquetes y dependecias de Bootstrap. Ahora solo falta configurarlo dentro de rails

En **config/webpack/environment.js** agrega lo siguiente:


```js
const { environment } = require('@rails/webpacker')

const webpack = require('webpack')
environment.plugins.append('Provide', new webpack.ProvidePlugin({
  $: 'jquery',
  jQuery: 'jquery',
  Popper: ['popper.js', 'default']
}))

module.exports = environment
```

La primera y ultima linea ya esta en este archivo así que asegurate que el archivo contiene este codigo.


Ahora en **app/javascript/packs/application.js** y debajo de `require("channels")`  agrega lo siguiente:

```
import 'bootstrap'
import '../stylesheets/application'
```

Crea la carpeta **app/javascript/stylesheets** con el archivo `application.scss` y agraga:

```
@import '~bootstrap/scss/bootstrap';
```

Finalmente falta solamente abrir el archivo  **app/views/layouts/application.html.erb** y debajo de:


```rhtml
<%= stylesheet_link_tag 'application', media: 'all', 'data-turbolinks-track': 'reload' %>
````

agregar:

```rhtml
<%= stylesheet_pack_tag 'application', media: 'all', 'data-turbolinks-track': 'reload' %>
```

De pronto te diste cuenta que estamos usando un archivo con una extension `.scss`. Este tipo de archivo es para manejar un tipo de CSS que se llama SASS.

- **Sass** (acrónimo de Syntactically Awesome StyleSheets) es una extensión de CSS que añade características muy potentes y elegantes a este lenguaje de estilos. Sass permite el uso de variables, reglas CSS anidadas, mixins, importación de hojas de estilos y muchas otras características, al tiempo que mantiene la compatibilidad con CSS.


## 6. Añade elementos de Bootstrap a la página

### ¡Añade un contenedor a tu aplicación!

**views/layouts/application.html.erb**

Dentro de la etiqueta `<body>`, reemplaza

```rhtml
<%= yield %>
```

por...

```rhtml
<div class="container">
  <%= yield %>
</div>
```

### Crea un parcial de encabezado

Por convención un parcial es un archivo de plantilla cuyo nombre empieza por un guion bajo y cuyo contenido se reutiliza en varias plantillas diferentes. Aquí el encabezado es un ejemplo de contenido que se repite en varias páginas.

Crea el archivo **app/views/layouts/_header.html.erb**


### Añade la barra de navegación

**app/views/layouts/_header.html.erb**

```rhtml
<nav class="navbar navbar-expand-lg ">
  <div class="container">
    <%= link_to "Instagram", root_path, class: "navbar-brand" %>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav ml-auto">
        <li class="nav-item">
          <%= link_to "Home", root_path, class: "nav-link" %>
        </li>
        <li class="nav-item">
          <%= link_to "Quiénes somos", about_path, class: "nav-link" %>
        </li>
      </ul>
    </div>
  </div>
</nav>
```

**NOTA** **Embedded Ruby?** -- **¿Ruby embebido?**

En Ruby se usa mucho ERB como sistema de plantillas para crear archivos HTML con código Ruby embebido.

En HTML, un enlace es así:

```html
<a href="#"> aquí </a>
```

Estas son etiquetas de Ruby:

```erb
< % = % >
```

En Ruby on Rails un enlace se verá así:

```erb
<%= link_to "aquí", "#" %>
```

### Añade el parcial de encabezado a la página de inicio

**app/views/layouts/application.html.erb**

Después de la etiqueta `<body>` inserta:

```erb
<%= render 'layouts/header' %>
```


### Añade el contenido del home

Reemplaza todo el contenido del archivo

**views/pages/home.html.erb**

```rhtml
<div class="jumbotron text-center">
  <h2>¡Bienvenidos a Instagram!</h2>
  <p>
   <%= link_to "Iniciar sesión", "#", class: "btn btn-default btn-lg" %>
   <%= link_to "Regístrate", "#", class: "btn btn-primary btn-lg" %>
  </p>    
</div>
```

## 8. Personalicemos Bootstrap

### Cambios de estilo

Ahora agregamos un poco de estilos CSS (*usando SASS*).

**app/javascript/stylesheets/application.scss**

Reemplaza:

```scss
@import '~bootstrap/scss/bootstrap';
```

por los siguientes estilos:

```scss
@import url(http://fonts.googleapis.com/css?family=Lato:400,700);
@import url(http://fonts.googleapis.com/css?family=Oleo+Script);

$body-bg:                          #fafafa !important;
$font-family-sans-serif:           'Lato', 'Helvetica Neue', Helvetica, Arial, sans-serif;
$primary:                          #3897F0;
$jumbotron-bg:                     white;

@import '~bootstrap/scss/bootstrap';

.navbar {
  background-color: #fff;
  font-weight: bold;
  height: 77px;
  border-bottom: 1px solid #dbdbdb;
}

.navbar-brand {
  font-family: 'Oleo Script', cursive;
  font-size: 25px;
  color: #262626;
}

.navbar-nav {
  font-weight: bold;
}
```


## 9. Añadir Devise para Autenticación de usuarios

### Añade la gema de Devise

*"Las gemas en Ruby son las bibliotecas o paquetes (código Ruby empaquetado de una manera predeterminada) de software que se instalan en el sistema para aumentar las funcionalidades del interprete"*.

La mayoria de las aplicaciones web necesitan que los usuarios puedan crear una cuenta, modificar su perfil, iniciar y cerrar sesión. En el contexto de rails hay una gema que se integra naturalmente con él y gestiona estos componentes; esta gema se llama Devise.

**/Gemfile**

Debajo de `'bootsnap', '>= 1.4.2', require: false` añade la gema de Devise.


```ruby
[...]
gem 'devise'
[...]
```

### Siempre pare el servidor con `CONTROL + C` y corre `bundle install` para instalar una nueva gema

Ejecuta bundle install para instalarla

`consola`

```bash
CONTROL + C
bundle install
```

### Vuelve a iniciar el servidor

`consola`

```bash
rails server
```


## 10. Configuración de Devise

**NOTA** El primer tab de tu consola todavía tiene el servidor de Rails corriendo.
Sigue usando el otro tab.


### Instala Devise

Ejecuta el generador de Devise:

`consola`

```bash
rails generate devise:install
```

Acabamos de crear los archivos necesario para la configuracion de Devise.
Ademas Devise nos deja una serie de recomendaciones sobre buenas practicas y configuraciones adicionales de la gema. Ahora podemos crear las vistas.


### Crea las vistas de Devise

Generar las vistas para la personalización del manejo de sesiones de usuario.
Estas vistas coresponden a las que necesitamos para iniciar y cerrar session, manejar registras de usuarios, cambio de contraseña...etc


`consola`

```
rails g devise:views
```

Y vemos que Rails acaba de crear varios archivos nuevos en nuestra aplicación.


### Crea un modelo de usuario

Los modelos en Rails usan un nombre en singular, y sus correspondientes tablas de base de datos usan un nombre en plural. Rails provee un generador para crear modelos, el cual la mayoría de desarrolladores en Rails tienden a usar para crear nuevos modelos. En nustro caso Devise ofrece un generador especifico que crea el modelo de usuario definiendo la base de nustro sistema de autenticación.

`consola`

```bash
rails generate devise User
```

Esta línea crea un modelo de usuario y un nuevo archivo: **app/models/user.rb**

Ve a **db/migrate** y deberías tener en los archivos algo así como **db/migrate/20191021001811_devise_create_users.rb**

El número es la fecha de creacíon.


### Migra la base de datos

`consola`

```bash
rails db:migrate
```

Este comando toma el archivo de migración y lo ejecuta, de manera que genere tablas en la base de datos.

**NOTA**
Las migraciones nos permiten hacer cambios sobre el esquema de la base de datos de forma iterativa y consistente.
Una migración es un archivo que se crea dentro de la carpeta **db/migrate** y que contiene instrucciones para modificar el esquema de la base de datos (crear tablas, agregar columnas, eliminar columnas, eliminar tablas, etc.).
Cuando creas un modelo desde la línea de comandos con el generador de Rails, automáticamente se crea una migración con las instrucciones para crear la tabla.


### Vuelve a iniciar el servidor

```bash
CONTROL + C (para parar el servidor)
rails server (para volver a iniciar el servidor)
```

Tendrás que reiniciar la aplicación cada vez que instales una gema o cada vez que ejecutes `rails db:migrate`



## 11. Mensajes flash

Los mensajes flash son los mensajes en sitios web que dicen "Gracias por registrarse en ..." o "Gracias por suscribirse a ..."

**app/views/layouts/application.html.erb**

Agrega lo siguiente Debajo de `<div class="container">` y antes de `<%= yield %>`:

```rhtml

<% flash.each do |name, msg| %>
  <% if msg.is_a?(String) %>
    <div class="alert alert-<%= name.to_s == 'notice' ? 'success' : 'danger' %> fade in">
      <button type="button" class="close" data-dismiss="alert" aria-hidden="true">&times;</button>
      <%= content_tag :div, msg, :id => "flash_#{name}" %>
    </div>
  <% end %>
<% end %>

```

## 12. Registrar nuevos usuarios o iniciar sesión

### Modifica la vista de inicio

**app/views/pages/home.html.erb**

¡Actualicemos la página de inicio!

```rhtml
<div class="jumbotron text-center">
 <h2>¡Bienvenidos a Instagram!</h2>
 <% if user_signed_in? %>
      # haz algo
 <% else %>
   <p>
     <%= link_to "Iniciar sesión", new_user_session_path, class: "btn btn-default btn-lg" %>
     <%= link_to "Regístrate", new_user_registration_path, class: "btn btn-primary btn-lg" %>
   </p>
  <% end %>  
</div>
```

### Modifica el parcial de navegación

**app/views/layout/_header.html.erb**

Reemplaza

```rhtml
<ul class="navbar-nav ml-auto">
  <li class="nav-item">
    <%= link_to "Home", root_path, class: "nav-link" %>
  </li>
  <li class="nav-item">
    <%= link_to "Quiénes somos", about_path, class: "nav-link" %>
  </li>
</ul>
```
por

```rhtml
<ul class="navbar-nav ml-auto">
  <li class="nav-item">
    <%= link_to "Home", root_path, class: "nav-link" %>
  </li>
  <li class="nav-item">
    <%= link_to "Quiénes somos", about_path, class: "nav-link" %>
  </li>
  <% if user_signed_in? %>
    <li class="nav-item">
      <%= link_to "Cerrar sesión", destroy_user_session_path, class: "nav-link", method: :delete %>
    </li>
  <% else %>
    <li class="nav-item">
      <%= link_to "Regístrate", new_user_registration_path, class: "nav-link" %>
    </li>
    <li class="nav-item">
      <%= link_to "Iniciar sesión", new_user_session_path, class: "nav-link" %>
    </li>
  <% end %>
</ul>
```

**NOTA** Usa el tabulador, la tecla Tab (Tab ↹) nos permite indentar el texto que este en nuestra selección y así mantener el código organizado y indentado.


## 13. Cambia las vistas de Devise

Cunado corrimos el comando `rails g devise:views` el generador creo un serie de vistas con formularios responsable del registro de usuario, el inicio de sesion etc.
Todos estas vistas están ubicadas dentro de la carpeta **app/views/devise**.
Ahora vamos a mejorar un poco estos archvos agregando CSS de Bootstrap.


### Reemplaza el código para cada una de las vistas de Devise

**app/views/devise/registrations/new.html.erb**

*Esta vista se encarga del formulario de registro de usuarios en tu app.*

```rhtml
<div class="form-wrapper">
  <h1>Regístrate</h1>

  <%= form_for(resource, as: resource_name, url: registration_path(resource_name)) do |f| %>
    <%= devise_error_messages! %>

    <div class="form-group">
      <%= f.label :email %>
      <%= f.email_field :email, autofocus: true, class: "form-control" %>
    </div>

    <div class="form-group">
      <%= f.label :password %>
      <%= f.password_field :password, class: "form-control" %>
    </div>

    <div class="form-group">
      <%= f.submit "Regístrate", class: "btn btn-success" %>
    </div>
  <% end %>

  <div class="form-group text-center">
    <%= render "devise/shared/links" %>
  </div>
</div>
```

**app/views/devise/registrations/edit.html.erb**

*Esta vista se encarga del formulario de edición de la información de usuarios en tu app.*

```rhtml
<div class="form-wrapper">
  <h1>Editar <%= resource_name.to_s.humanize %></h1>

  <%= form_for(resource, :as => resource_name, url: registration_path(resource_name), html: { method: :put }) do |f| %>
    <%= devise_error_messages! %>

    <div class="form-group">
      <%= f.label :email %>
      <%= f.email_field :email, class: "form-control", autofocus: true %>
    </div>

    <div class="form-group">
      <%= f.label :password %> <i>(déjala en blanco si no quieres cambiarla)</i>
      <%= f.password_field :password, class: "form-control", autocomplete: "off" %>
    </div>

    <div class="form-group">
      <%= f.label :current_password %> <i>(necesitamos tu contraseña actual para confirmar los cambios)</i>
      <%= f.password_field :current_password, class: "form-control" %>
    </div>

    <div class="form-group">
      <%= f.submit "Actualizar", class: "btn btn-success" %>
    </div>
  <% end %>

  <h3>Cancelar mi cuenta</h3>

  <p>Unhappy? <%= button_to "Cancelar mi cuenta", registration_path(resource_name), data: { confirm: "¿Estás segura/o?" }, method: :delete, class: "btn btn-warning" %></p>

  <%= link_to "Volver", :back %>
</div>
```

**app/views/devise/passwords/new.html.erb**

*Esta vista está encargada de mostrar el formulario para la solicitud de contraseña al sistema en caso de olvido.*

```rhtml
<div class="form-wrapper">
  <h1>¿Olvidaste tu contraseña?</h1>

  <%= form_for(resource, as: resource_name, url: password_path(resource_name), html: { method: :post }) do |f| %>
    <%= devise_error_messages! %>

    <div class="form-group">
      <%= f.label :email %>
      <%= f.email_field :email, class: "form-control", autofocus: true %>
    </div>

    <div class="form-group">
      <%= f.submit "Envíame las instrucciones para restablecer mi contraseña", class: "btn btn-success" %>
    </div>
  <% end %>

  <div class="form-group text-center">
    <%= render "devise/shared/links" %>
  </div>
</div>
```

**app/views/devise/passwords/edit.html.erb**

*En esta vista se encuentra el formulario para el cambio de la contraseña de un usuario de tu app*

```rhtml
<div class="form-wrapper">
  <h1>Cambia tu contraseña</h1>

  <%= form_for(resource, as: resource_name, url: password_path(resource_name), html: { method: :put }) do |f| %>
    <%= devise_error_messages! %>
    <%= f.hidden_field :reset_password_token %>

    <div class="form-group">
      <%= f.label :password, "Nueva contraseña" %>
      <%= f.password_field :password, class: "form-control", autofocus: true %>
    </div>

    <div class="form-group">
      <%= f.label :password_confirmation, "Confirmar nueva contraseña" %>
      <%= f.password_field :password_confirmation %>
    </div>

    <div class="form-group">
      <%= f.submit "Cambiar mi contraseña", class: "btn btn-success" %>
    </div>
  <% end %>

  <div class="form-group text-center">
    <%= render "devise/shared/links" %>
  </div>
</div>
```

**app/views/devise/sessions/new.html.erb**

*¡Este es el formulario de login (inicio de sesión) de tu Instagram app!*

```rhtml
<div class="form-wrapper">
  <h1>Iniciar Sesion</h1>
  <%= form_for(resource, :as => resource_name, :url => session_path(resource_name)) do |f| %>
    <div class="form-group">
      <%= f.label :email %>
      <%= f.email_field :email, class: "form-control", autofocus: true %>
    </div>

    <div class="form-group">
      <%= f.label :password %>
      <%= f.password_field :password, class: "form-control" %>
    </div>

    <div class="checkbox">
      <%= f.check_box :remember_me %>
      <%= f.label :remember_me %>
    </div>

    <div class="form-group">
      <%= f.submit "Ingresa", class: "btn btn-success" %>
    </div>
  <% end %>

  <div class="form-group text-center">
    <%= render "devise/shared/links" %>
  </div>
</div>
```

### Añade estos estilos para que tus formularios se vean más geniales <3

Al final del archivo: **app/javascript/stylesheets/application.scss**

```css
.form-wrapper {
  width: 60%;
  margin: 20px auto;
  background-color: #fff;
  padding: 40px;
  border: 1px solid #eeefef;
  border-radius: 3px;
}
```

### Añade un enlace "Mi cuenta" al parcial de navegacíon

**app/views/layouts/_header.html.erb**

Debajo de `<% if user_signed_in? %>`:

```rhtml
<li class="nav-item">
  <%= link_to "Mi cuenta", edit_user_registration_path, class: "nav-link" %>
</li>

```

Ya tenemos todo un sistema de registro, autenticacion de usuarios con notificaciones super poderoso. Si quieres conocer mas acerca de como configurar y usar Devise mas alla de esta guia encontraras un enlace al final de la guia.


## 14. Genera el scaffold para Posts

`Posts` serán nuestras publicaciones o, mejor dicho, ¡Las imágenes que publicamos en nuestro Instagram!


### Genera un scaffold para Posts

Un scaffold es un generador automático de modelo + controlador + vistas.
Scaffold significa andamio en inglés. Es un generador de código el cual nos permite tener las funcionalidades básicas de administración de un modelo, es decir el CRUD (Create, Read, Update, Delete), y que son típicas para cualquier sistema transaccional. Entonces ya tendremos dos modelo de datos, uno para los usuarios que creamos con Devise y ahora sus respectivos posts utilizando el generador de código scaffold.

`consola`

```bash
rails generate scaffold posts description:string
```

Con este comando le estamos diciendo a Rails de crear un scaffold `posts` con un campo `description` que es de tipo `string`. Por ahora nustra publicación de Instagram solo tiene una descripción.
Usando scaffold hemos creado todo el código necesario para un CRUD, éste nos ha creado los modelos, controladores, vistas, assets, rutas y las migraciones.

Hablando de migraciones, ahora tenemos que ejecutar la migración.

`consola`

```bash
rails db:migrate
```

**NOTA**
Las migraciones nos permiten hacer cambios sobre el esquema de la base de datos de forma iterativa y consistente.
Una migración es un archivo que se crea dentro de la carpeta **db/migrate** y que contiene instrucciones para modificar el esquema de la base de datos (crear tablas, agregar columnas, eliminar columnas, eliminar tablas, etc.).
Cuando creas un modelo desde la línea de comandos con el generador de Rails, automáticamente se crea una migración con las instrucciones para crear la tabla.


**IMPORTANTE**
El scaffold también crea un archivo de estilos CSS basicos pero nosotros vamos a usar nuestro propio CSS así que podemos borrar este archivo para no interferir con nuestros estilos.

Borra **/app/assets/stylesheets/scaffolds.scss**.


## 15. Simplifiquemos el controlador de Posts

**app/controllers/posts_controller.rb**

### Reemplaza todo el contenido del controlador

```ruby
class PostsController < ApplicationController
  before_action :set_post, only: [:show, :edit, :update, :destroy]

  def index
    @posts = Post.all
  end

  def show
  end

  def new
    @post = Post.new
  end

  def edit
  end

  def create
    @post = Post.new(post_params)
    if @post.save
      redirect_to @post, notice: '¡Post creado satisfactoriamente!'
    else
      render :new
    end
  end

  def update
    if @post.update(post_params)
      redirect_to @post, notice: '¡Post actualizado satisfactoriamente!'
    else
      render :edit
    end
  end

  def destroy
    @post.destroy
    redirect_to posts_url
  end

  private
    # Use callbacks to share common setup or constraints between actions.
    def set_post
      @post = Post.find(params[:id])
    end

    # Never trust parameters from the scary internet, only allow the white list through.
    def post_params
      params.require(:post).permit(:description)
    end
end
```

## 16. Las vistas de posts

### Esto se llama el parcial "formulario"

Las plantillas parciales (partials) son una forma de dividir el proceso de representación en partes más manejables. Los parciales permiten extraer fragmentos de código de sus plantillas en archivos separados y también reutilizarlos en todas sus plantillas.
Los parciales tienen como prefijo un subrayado, de manera de no confundirlas con vistas regulares

Modifica el parcial del formulario **apps/views/posts/_form.html.erb**

Reemplaza todo el contenido por:

```rhtml
<h1>Crear un post</h1>
<%= form_for(@post) do |f| %>
  <% if @post.errors.any? %>
    <div class="alert alert-danger alert-dismissable"><button aria-hidden="true" class="close" data-dismiss="alert" type="button">×</button>
      <ul class="list-unstyled">
        <% @post.errors.full_messages.each do |msg| %>
          <%= content_tag :li, msg, :id => "error_#{msg}" if msg.is_a?(String) %>
        <% end %>
      </ul>
    </div>
  <% end %>

  <div class="form-group">
    <%= f.label :description %>
    <%= f.text_field :description, class: "form-control" %>
  </div>
  <div class="form-group">
    <%= f.submit class: "btn btn-primary" %>
  </div>
<% end %>
```

### Para mantener nuestros estilos, tendremos el contenido de las siguientes vistas dentro de un form-wrapper

Cambia todo lo que hay en este archivos: **app/views/posts/new.html.erb** por:

```rhtml
<div class="form-wrapper">
  <h2>Crear un post</h2>
  <%= render 'form' %>
</div>
```

Y lo que hay en este archivo **app/views/posts/edit.html.erb** por

```rhtml
<div class="form-wrapper">
  <h2>Actualizar un post</h2>
  <%= render 'form' %>
</div>
```

### Añade un enlace en el navbar (barra de navegación) para crear un nuevo post

**app/views/layouts/_header.html.erb**

Debajo de `<% if user_signed_in? %>`:

```rhtml
<li class="nav-item">
  <%= link_to 'Nuevo post', new_post_path, class: "nav-link"%>
</li>
```

### Redireccionamos la raíz de nuestra aplicación al `index` de Posts

##### (no te diremos en qué archivo, es un desafío ;) , si tienes dudas, ¡Pregúntale a uno de tus mentores! )

reemplaza `root 'pages#home'` por `root 'posts#index'`


## 17. Posts, Usuarios y Asociaciones

### Asociaciones

Las asociaciones se utilizan para definir relaciones entre tablas de una base de datos. Existen dos tipos de asociaciones que se pueden modelar en una base de datos relacional:
- One to many (uno a muchos)
- Many to many (muchos a muchos)

En nustro ejemplo usaremos One to many (uno a muchos)

### One to many

En una relación uno a muchos cada registro de una tabla está relacionado a un registro de otra tabla.
Por ejemplo, imagina que cada publicación pertenece a un usuario.

### Configura tus asociaciones

Un Post `belongs_to` un Usuario.
Una Publicación ***pertenece*** a un Usuario.

En el model `Post` **app/models/post.rb** remplaza el contenido por:

```ruby
class Post < ActiveRecord::Base
	belongs_to :user
end
```

### Genera una nueva migración de índice de un usuario
<br/>
Esto significa que cada publicación estará relacionada con un usuario.

`consola`

```bash
rails generate migration add_user_id_to_posts user_id:integer:index
```

Y despues

```bash
rails db:migrate
```
* ##### Recuerda que hacemos `rails db:migrate` porque acabamos de crear una migración.

* ##### Cada vez que hagas una migración, debes reiniciar el servidor de Rails.

`consola`

```bash
CONTROL + C (para parar el servidor)
rails server (para volver a iniciar el servidor)
```


### Un Usuario `has_many` Posts

##### Un Usuario ***tiene*** muchas Publicaciones

En el modelo `User` **app/models/user.rb** remplaza el contenido por:

```ruby
class User < ActiveRecord::Base

  devise :database_authenticatable, :registerable,
         :recoverable, :rememberable, :validatable

  has_many :posts
end
```


## 18. Autorización: ¿Quién puede? ¿Quién no puede?

Una vez que un usuario tiene acceso a la plataforma, hay que ver los permisos que este usuario tiene.

- Tenemos que asegurar que un usuario no puede cambiar la publicación de otro usuario.

- También que las acciones (crear, cambiar o borrar una publicación) se puede hacer solamente si estas autenticado.


### Actualiza el controlador Posts

Ahora vamos a cambiar el codigo para que un usuario pueda crear, editar y borrar sus publicaciones y no aceder a todas.

**app/controllers/posts_controller.rb**

```ruby
class PostsController < ApplicationController
  before_action :set_post, only: [:show, :edit, :update, :destroy]

  def index
    @posts = Post.all
  end

  def show
  end

  def new
    @post = current_user.posts.build
  end

  def edit
  end

  def create
    @post = current_user.posts.build(post_params)
    if @post.save
      redirect_to @post, notice: '¡Post creado satisfactoriamente!'
    else
      render :new
    end
  end

  def update
    if @post.update(post_params)
      redirect_to @post, notice: '¡Post actualizado satisfactoriamente!'
    else
      render :edit
    end
  end

  def destroy
    @post.destroy
    redirect_to posts_url
  end

  private
    # Use callbacks to share common setup or constraints between actions.
    def set_post
      @post = Post.find_by(id: params[:id])
    end

    def correct_user
      @post = current_user.posts.find_by(id: params[:id])
      redirect_to posts_path, notice: "¡No estás autorizada/o para editar este post!" if @post.nil?
    end

    # Never trust parameters from the scary internet, only allow the white list through.
    def post_params
      params.require(:post).permit(:description)
    end
end
```

### Agreguemos autenticación de usuarios con Devise

Devise crea algunos métodos de ayuda y filtros para que puedas manejar la autenticación en tu aplicación.
El filtro que ppodemos agregar sobre los controladores que quieres proteger es el siguiente:

`before_action :authenticate_user!`

En nuestra aplicación vamos a proteger todas las acciones del controlador posts exceptuando `index` y `show` que son las que nos van a permitir listar y mostrar los detalles de una publicación.

Añade `before_action` al Controlador Posts

**app/controllers/posts_controller.rb**

Debajo de `before_action :set_post ...`

```ruby
before_action :authenticate_user!, except: [:index, :show]
```

### Añade el `:correct_user`

Añade el método `before_action` a tu controlador de Posts

**app/controllers/posts_controller.rb**

Debajo de `before_action :authenticate_user! ...`

```ruby
before_action :correct_user, only: [:edit, :update, :destroy]
```


## 19. Sube imágenes con Active Storage

ActiveStorage permite a los desarrolladores gestionar la carga de archivos, el almacenamiento en la nube y la gestión de documentos vinculados a modelos en todas sus aplicaciones.
En nustro ejemplo, Active Storage nos permite manejar la carga de imagen de cada publicación.


### Primer paso instalar Active Storage

Ejecuta el comando de instalación:

`consola`

```bash
rails active_storage:install
```

Y despues

```bash
rails db:migrate
```

Con estos comandos acabamos de instalar Active Storage y actualizar la base de datos con campos necesarios para almacenar archivos en nustra aplicación.


### Instalar image_processing

Ahora necesitamos instalar un libreria para procesar nuestras imagenes con las caracteriticas y el tamaño de las imagenes que se suben a Instagram, entonces agregaremos la gema `image_processing`.


Dentro del archivo **/gemfile** busca la linea `gem 'image_processing', '~> 1.2'` y quitale el `#` para que se vea de la siguiente forma:

```ruby
# Use Active Storage variant
gem 'image_processing', '~> 1.2'
```

Acabamos simplemente de remover un character que significa que esta linea es un comentario.
Ahora esta linea es parte del codigo y podemos ejecutar `bundle install` para instalar esta nueva gema.

`consola`

```bash
CONTROL + C (para parar el servidor)
bundle install
```

Y despues


```bash
rails server
```

Para iniciar el servidor otra vez.


### Actualiza Post

Actualiza el model `Post`

**/app/models/post.rb**

```ruby
class Post < ApplicationRecord
  belongs_to :user
  has_one_attached :image

  def squared_img
    if image.attached?
      image.variant(combine_options: { resize: '600x600^', gravity: 'center', extent: '600x600' })
    end
  end
end
```


### Edita el formulario de Post

**/app/views/posts/_form.html.erb**

Justo despues de

```rhtml
<div class="form-group">
    <%= f.label :description %>
    <%= f.text_field :description, class: "form-control" %>
  </div>
```

Añade:

```rhtml
  <div class="form-group">
    <%= f.label :image %>
    <%= f.file_field :image %>
  </div>
```

### Actualiza el controlador de Posts para parámetros "strong"

**/app/controllers/posts_controller.rb**

`def post_params`

```ruby
.
  def post_params
    params.require(:post).permit(:description, :image)
  end
.
```

Aqui estamos permitiendo que nuestro controlador pueda manejar un parametro adicional que se llama `image`.

### Actualiza la vista `index` de Posts

**/app/views/posts/index.html.erb**

```rhtml
<% if user_signed_in? %>
  <div class="main-wrapper">
    <div class="row">
      <% @posts.each do |post| %>
        <div class="col-xs-12 col-sm-6 col-md-4">
          <div class="image center-block">
            <%= link_to (image_tag post.squared_img, class:'img-fluid'), post_path(post) %>
          </div>
        </div>
      <% end %>
    </div>
  </div>
<% else %>
  <div class="jumbotron text-center">
   <h1>¡Bienvenidos a Instagram!</h1>
     <p>
       <%= link_to "Iniciar sesión", new_user_session_path, class: "btn btn-default btn-lg" %>
       <%= link_to "Regístrate", new_user_registration_path, class: "btn btn-primary btn-lg" %>
     </p>
  </div>
<% end %>
```

### Actualiza la vista `show` de Posts

**/app/views/posts/show.html.erb**

```rhtml
<div class="posts-wrapper row">
  <div class="post">
    <div class="image center-block">
      <%= image_tag @post.squared_img, class:'img-responsive' %>
    </div>
    <div class="post-head">
      <div class="name">
        <%= @post.user.email if @post.user %>
      </div>
    </div>
    <p class="description">
      <%= @post.description %>
    </p>
  </div>
</div>
```

### Con el estilo Instagram

Abajo del archivo **app/javascript/stylesheets/application.scss** agregamos:

```css

.main-wrapper {
  margin-top: 100px
}

.posts-wrapper {
  padding-top: 40px;
  margin: 0 auto;
  max-width: 642px;
  width: 100%;
}

.post {
  background-color: #fff;
  border-color: #edeeee;
  border-style: solid;
  border-radius: 3px;
  border-width: 1px;
  margin-bottom: 60px;
}

.post-head {
  height: 64px;
  padding: 14px 20px;
  color: #125688;
  font-size: 15px;
  line-height: 18px;
  .thumbnail {}
  .name {
    display: block;
  }
}

.image {
  padding-bottom: 30px;
}

.description {
  padding: 24px 24px;
  font-size: 15px;
  line-height: 18px;
}
```



## 20. Editar y borrar Posts

### Ahora queremos editar nuestros posts

**app/views/posts/show.html.erb**

Dentro de `<div class="post">` abajo colocamos:

```rhtml
<div class="text-center edit-links">
  <%= link_to "← Volver", posts_path %>
  |
  <%= link_to "Editar Post", edit_post_path(@post) %>
</div>
```

y añade los siguientes estilos

**app/javascript/stylesheets/application.scss**

```css
.edit-links {
  margin-top: 20px;
  margin-bottom: 40px;
}
```

y en **app/views/posts/edit.html.erb**, lo más arriba, añade

```rhtml
<div class="text-center">
  <%= image_tag @post.squared_img %>
</div>
```

### ¿Y si queremos borrar nuestro post?

**app/views/posts/edit.html.erb**

Completamente abajo colocamos:

```rhtml
<div class="text-center edit-links">
  <%= link_to "Borrar Post", post_path(@post), method: :delete, data: { confirm: "¿Estás segura que quieres eliminar este post?" } %>
  |
  <%= link_to "cancelar", posts_path %>
</div>
```

## 21. Añade un nombre de usuario para personalizar la aplicación

### Crea la migración en la base de datos

`consola`

```bash
rails generate migration AddNameToUsers name:string
```

### Migra la base de datos

`consola`

```bash
rails db:migrate
```

### Vuelve a iniciar el servidor después de correr una migración

`consola`

```bash
CONTROL + C
rails server
```

### Indica a Devise autorizar este nuevo parámetro  

Actualiza **app/controllers/application_controller.rb**


```ruby
class ApplicationController < ActionController::Base
 protect_from_forgery with: :exception
 before_action :configure_permitted_parameters, if: :devise_controller?

protected

  def configure_permitted_parameters
    devise_parameter_sanitizer.permit(:sign_up, keys: [:name])
    devise_parameter_sanitizer.permit(:account_update, keys: [:name])
  end
end
```

### Y también agregamos el campo en las vistas

**app/views/devise/registrations/new.html.erb**, **app/views/devise/registrations/edit.html.erb**

Justo antes de

```rhtml
<div class="form-group">
  <%= f.label :email %>
```

Añade

```rhtml
.
  <div class="form-group">
    <%= f.label :name %>
    <%= f.text_field :name, autofocus: true, class: "form-control" %>
  </div>
.
```

### Terminamos con un nuevo controlador

Crea el archivo **app/controllers/registrations_controller.rb**:

```ruby
class RegistrationsController < Devise::RegistrationsController

  private

  def sign_up_params
    params.require(:user).permit(:email, :name, :password, :password_confirmation)
  end

  def account_update_params
    params.require(:user).permit(:email, :name, :password, :password_confirmation, :current_password)
  end
end  
```

### Corrige la ruta

**/config/routes.rb**

Reemplaza

```ruby
devise_for :users
```

con...

```ruby
devise_for :users, :controllers => { registrations: 'registrations' }
```

### Ahora cambiamos el correo por el nombre

**app/views/posts/show.html.erb**

Reemplaza

```rhtml
<%= @post.user.email if @post.user %>
``

con...

```rhtml
<%= @post.user.name if @post.user %>
```

## 22. Protege tus posts

### Rodea el enlace de edición con un "si" condicional

De esta manera sólo se pueden ver tus posts. Para poner esto de otra manera: Un usuario sólo puede editar (o borrar) sus posts (y no los posts de otros usuarios ). ¿Tiene algun sentido?


**app/views/posts/show.html.erb**

Reemplaza

```rhtml
<div class="text-center edit-links">
  <%= link_to "← Volver", posts_path %>
    |
  <%= link_to "Editar Post", edit_post_path(@post) %>
</div>
```

con

```rhtml
<% if @post.user == current_user %>
  <div class="text-center edit-links">
    <%= link_to "← Volver", posts_path %>
    |
    <%= link_to "Edit post", edit_post_path(@post) %>
  </div>
<% else %>
  <div class="text-center edit-links">
    <%= link_to "← Volver", posts_path %>
  </div>
<% end  %>
```


## 23. Añadiremos la opción de comentar posts

### Empezamos por generar un modelo

`consola`

```bash
rails g model Comment user:references post:references content:text
```

Este comando nos genera una migración **db/migrate/** para añadir los campos en la base de datos y un modelo **app/model/comment.rb**.

### Migra la base de datos

`consola`

```bash
rails db:migrate
```

### Vuelve a iniciar el servidor después de correr una migración

`consola`

```bash
CONTROL + C
rails server
```

### Asocia los comentarios

Ahora nuestro modelo **app/model/comment.rb** debe estar configurado para indicar a quién pertenecen los comentarios.

```ruby
class Comment < ActiveRecord::Base  
  belongs_to :user
  belongs_to :post
end
```

Aquí estas lineas indican que un comentario pertenece a un `user` y también pertenece a un `post`.

Por último, en **app/models/user.rb** and **app/models/post.rb** añade la siguiente línea a cada uno:

```ruby
has_many :comments, dependent: :destroy
```

### Crea la ruta para los comentarios

En **config/routes.rb** Reemplaza

```ruby
resources :posts
```
con...

```ruby
resources :posts do  
  resources :comments
end
```

### Para terminar con la lógica, creamos el controlador

`consola`

```bash
rails g controller comments
```

El controlador de comentarios solo va a tener las acciones de crear y borrar comentarios.

Actalualiza **app/controllers/comments_controller.rb** con:

```ruby
class CommentsController < ApplicationController
  before_action :set_post

  def create  
    @comment = @post.comments.build(comment_params)
    @comment.user_id = current_user.id

    if @comment.save
      flash[:success] = "¡Has comentado este post!"
      redirect_back fallback_location: root_path
    else
      flash[:alert] = "Revisa el formulario de comentarios, algo salió mal :/"
      render root_path
    end
  end

  def destroy  
    @comment = @post.comments.find(params[:id])

    @comment.destroy
    flash[:success] = "Comentario eliminado :("
    redirect_back fallback_location: root_path
  end

  private

  def comment_params  
    params.require(:comment).permit(:content)
  end

  def set_post  
    @post = Post.find(params[:post_id])
  end
end
```

## 24. Las vistas y los estilos de los comentarios


Reemplaza **app/views/posts/show.html.erb**

```rhtml
<div class="posts-wrapper">
  <div class="post">
    <div class="image center-block">
      <%= image_tag @post.squared_img, class:'img-fluid' %>
    </div>
    <div class="post-bottom">
      <div class="description">
        <div class="user-name">
          <%= @post.user.name %>
        </div>
        <%= @post.description %>
      </div>
      <% if @post.comments %>
        <% @post.comments.each do |comment| %>
          <div class="comment">
            <div class="user-name">
              <%= comment.user.name %>
            </div>
            <div class="comment-content">
              <%= comment.content %>
            </div>
            <% if comment.user == current_user %>
              <%= link_to post_comment_path(@post, comment), method: :delete, data: { confirm: "¿Estás segura?" } do %>
                <span class="glyphicon glyphicon-remove delete-comment"></span>
              <% end %>
            <% end %>
          </div>
        <% end %>
      <% end %>
    </div>
    <div class="comment-like-form row">
      <div class="like-button col-sm-1">
        <span class="glyphicon glyphicon-heart-empty"></span>
      </div>
      <div class="comment-form col-sm-11">
        <%= form_for [@post, @post.comments.new] do |f| %>
          <div class="form-group">
            <%= f.text_field :content, class: 'form-control', placeholder: 'Añade un comentario...' %>
          </div>
        <% end %>
      </div>
    </div>
  </div>
</div>
<% if @post.user.id == current_user.id %>
  <div class="text-center edit-links">
    <%= link_to "Cancelar", posts_path %>
    |
    <%= link_to "Editar el post", edit_post_path(@post) %>
  </div>
<% else %>
  <div class="text-center edit-links">
    <%= link_to "← Volver", posts_path %>
  </div>
<% end %>
```

### Los estilos para ponerlo bonito

En **app/javascript/stylesheets/application.scss**

Borra los estilos debajo de

```css
.navbar-brand {
  font-weight: bold;
}
```

Y reemplaza con

```css

.main-wrapper {
  margin-top: 100px
}

.image {
  padding-bottom: 30px;
}

.posts-wrapper {
  padding-top: 40px;
  margin: 0 auto;
  max-width: 642px;
  width: 100%;
}

.post {
  background-color: #fff;
  border-color: #edeeee;
  border-style: solid;
  border-radius: 3px;
  border-width: 1px;
  margin-bottom: 60px;
  .post-head {
    flex-direction: row;
    height: 64px;
    padding-left: 24px;
    padding-right: 24px;
    padding-top: 24px;
    color: #125688;
    font-size: 15px;
    line-height: 18px;
    .user-name, .time-ago {
      display: inline;
    }
    .user-name {
      font-weight: 500;
    }
    .time-ago {
      color: #A5A7AA;
      float: right;
    }
  }
}

.post-bottom {
  .user-name, .comment-content {
    display: inline;
  }
  .description {
    margin-bottom: 7px;
  }
  .user-name {
    font-weight: 500;
    margin-right: 0.3em;
    color: #125688;
    font-size: 15px;
  }
  .user-name, .caption-content {
    display: inline;
  }
  .comment {
    margin-top: 7px;
    .user-name {
      font-weight: 500;
      margin-right: 0.3em;
    }
    .delete-comment {
      float: right;
      color: #515151;
    }
  }
  margin-bottom: 7px;
  padding-top: 24px;
  padding-left: 24px;
  padding-right: 24px;
  padding-bottom: 10px;
  font-size: 15px;
  line-height: 18px;
}

.comment_content {
  font-size: 15px;
  line-height: 18px;
  border: medium none;
  width: 100%;
  color: #4B4F54;
}

.comment-like-form {
  padding-top: 24px;
  margin-top: 13px;
  margin-left: 24px;
  margin-right: 24px;
  min-height: 68px;
  align-items: center;
  border-top: 1px solid #EEEFEF;
  flex-direction: row;
  justify-content: center;
}

.form-wrapper {
  width: 60%;
  margin: 20px auto;
  background-color: #fff;
  padding: 40px;
  border: 1px solid #eeefef;
  border-radius: 3px;
}

.edit-links {
  margin-top: 20px;
  margin-bottom: 40px;
}
```

## 25. Control de versiones y Github

**Recursos:**
[Control de versiones con Git y GitHub](http://wikis.fdi.ucm.es/ELP/Control_de_versiones_con_Git_y_GitHub)

¡Ahora veremos en secuencia los pasos necesarios para subir tu primer proyecto a la plataforma Github!

1. En la parte superior derecha de tu espacio de trabajo en [C9](http://c9.io), haz clic en tu foto para abrir el panel de configuración y clic en `Dashboard`.
[https://c9.io/account/ssh](https://c9.io/account/ssh)
2. Ahora click en el círculo de arriba que tiene un engranaje y después en el menú lateral que dice `SSH keys`
3. Copia todas las líneas que empiezan por `ssh-rsa...`
4. Crea una cuenta en GitHub: [https://github.com](https://github.com)
5. Entra en [tu perfil de usuario](https://github.com/settings/profile) y haz clic en `SSH and GPG keys`.
[https://github.com/settings/ssh](https://github.com/settings/ssh)
6. Ahora clic en “Add SSH Key”. Introduce el título: "C9", pega la clave SSH en el cuadro "key", y haz clic en "Add key".
7. Crea un repositorio nuevo vacío para tu nuevo proyecto. Desde tu repositorio, copia el enlace SSH:
```
git@github.com:sunombre/nombredelproyecto.git
```
8. Convierte tu directorio actual en un repositorio git ejecutando en la consola de C9:
```
git init
```
9. Utilizando el enlace SSH que copiaste en el paso 7, añade el repositorio remoto como origen:
```
git remote add origin git@github.com:sunombre/nombredelproyecto.git
```
10. Añade tus archivos y haz commit
```
git add .
```
```
git commit -m "Mi Primer commit"
```
11. Sube los archivos:
```
git push -u origin master
```

**Ahora tienes tu repositorio actualizado en GitHub**



## 26. Tener nuestra aplicación en la web

¿Cómo subir nuestra aplicación en la web, de forma que otros puedan verla? Con un servicio llamado [Heroku](http://heroku.com) que permite subir tu aplicación en un servidor gratis en cuestión de segundos.

### Regístrate en Heroku

[https://www.heroku.com/](https://www.heroku.com/)

### C9 ya tiene una herramienta que se llama Heroku toolbelt. Solo necesitamos actualizarla

```bash
wget -O- https://toolbelt.heroku.com/install-ubuntu.sh | sh
```

### Inicia sesión en Heroku desde la consola

```bash
heroku login
Email: (Introduce tu correo electrónico)
Password ( Introduce tu contraseña - se mostrará en blanco y es normal )
```

### Añade las claves a Heroku

```bash
heroku keys:add
heroku create #crea una nueva URL para la aplicación
```

### Añade las nuevas gemas y grupos de gemas para Heroku

**/gemfile**

```ruby
group :development, :test do
     gem 'sqlite3'
end

group :production do
     gem 'pg'
     gem 'rails_12factor'
end
```

Nota: Después de crear un grupo `producción` a tu Gemfile, debes cambiar a utilizar `bundle install --without production`

### Entonces instalamos las gemas

```bash
bundle install --without production
```

### El baile de git

```bash
git add --all
git commit -m "¡Lista para subir a Heroku!"
git push origin master
```

### Sube a Heroku

```bash
git push heroku master
heroku open
heroku rename instagram #Reemplaza "instagram" con el nombre de tu proyecto
heroku run rails db:migrate #Para correr las migraciones
```

## Bonus: Comentarios con AJAX

¿Cómo intercambiar información con el servidor sin tener que refrescar la página? Ese es el problema que soluciona [Ajax](https://es.wikipedia.org/wiki/AJAX).
En nuestro caso sería como añadir comentarios sin tener que refrescar la página.

- recursos: [JavaScript, jQuery y Ajax](http://blog.makeitreal.camp/javascript-jquery-y-ajax)


## 27.  Mueve los comentarios en un parcial

Ajax en Rails se maneja con parciales, entonces crea un nuevo archivo

**app/views/comments/_comment.html.erb**

```rhtml
<div class="comment" id="comment_<%= comment.id %>">
  <div class="user-name">
    <%= comment.user.name %>
  </div>
  <div class="comment-content">
    <%= comment.content %>
  </div>
  <% if comment.user == current_user %>
    <%= link_to post_comment_path(post, comment), method: :delete, data: { confirm: "¿Estás segura?" } do %>
      <span class="glyphicon glyphicon-remove delete-comment"></span>
    <% end %>
  <% end %>
</div>
```

### Ahora podemos cambiar `show.html.erb`

Acabamos de mudar el comentario aparte en un archivo separado. Ahora, vamos a tener que ajustar nuestro `show` para seguir monstrando los comentarios de manera apropiada.

En **app/views/posts/show.html.erb**

Reemplaza

```rhtml
<% @post.comments.each do |comment| %>
  <div class="comment">
    <div class="user-name">
      <%= comment.user.name %>
    </div>
    <div class="comment-content">
      <%= comment.content %>
    </div>
    <% if comment.user == current_user %>
      <%= link_to post_comment_path(@post, comment), method: :delete, data: { confirm: "¿Estás segura?" } do %>
        <span class="glyphicon glyphicon-remove delete-comment"></span>
      <% end %>
    <% end %>
  </div>
<% end %>
```

con...


```rhtml
<%= render @post.comments, post: @post %>
```

Y sigue funcionando igual.

### Añadiendo `remote: true` a nuestro formulario

En **app/views/posts/show.html.erb**

reemplaza

```rhtml
<% if post.comments %>
  <%= render @post.comments, post: @post %>
<% end %>
```

con...

```rhtml
<div class="comments" id="comments_<%= @post.id %>">
  <% if @post.comments %>
    <%= render @post.comments, post: @post %>
  <% end %>
</div>
```

y las líneas

```rhtml
<%= form_for [@post, @post.comments.new] do |f| %>
  <%= f.text_field :content, placeholder: 'Añade un comentario...' %>
<% end %>
```

con...

```rhtml
<%= form_for([@post, @post.comments.build], remote: true) do |f| %>
  <%= f.text_field :content, placeholder: 'Añade un comentario...', id: "comment_content_#{@post.id}" %>
<% end %>
```

### Tenemos que ajustar también el controlador

**app/controllers/comments_controller.rb**

Reemplaza el `action` para crear con:

```ruby
def create
  @comment = @post.comments.build(comment_params)
  @comment.user_id = current_user.id

  if @comment.save
    respond_to do |format|
      format.html { redirect_to root_path }
      format.js
    end
  else
    flash[:alert] = "Revisa el formulario de comentarios, algo salió mal :/"
    render root_path
  end
end
```

### Creamos la respuesta Javascript

¡jQuery al rescate!
Crea un nuevo archivo en la carpeta **app/views/comments/** un archivo **create.js.erb**. En ese archivo, agrega la siguiente combinación de Javascript / Ruby

```erb
$('#comments_<%= @post.id %>').append("<%=j render 'comments/comment', post: @post, comment: @comment %>");
$('#comment_content_<%= @post.id %>').val('')
```

### Ahora también para borrar comentarios

Añadir `remote: true` al enlace para borrar

**app/views/comments/_comment.html**

Al final de esta línea y antes de `do`, añade `, remote: true`

```rhtml
<%= link_to post_comment_path(post, comment), method: :delete, data: { confirm: "¿Estás segura?" } do %>
```

Quedaría:

```rhtml
<%= link_to post_comment_path(post, comment), method: :delete, data: { confirm: "¿Estás segura?" }, remote: true do %>
```

### Añade la respuesta Javascript para la acción del controlador

Al igual que antes, ahora podemos asegurar que rails responde no sólo con HTML, sino también con Javascript.

Añade el método `responds_to` a la acción `destroy` dentro del `comments_controller`

```ruby
def destroy
  @comment = @post.comments.find(params[:id])

  if @comment.user_id == current_user.id
   @comment.delete
   respond_to do |format|
     format.html { redirect_to root_path }
     format.js
   end
  end
end
```

Y por último pero no menos importante..

### Finalizar con jQuery

¡Simplemente estamos añadiendo nuestra lista de comentarios actualizada!

Crea el nuevo archivo **destroy.js.erb** dentro de la carpeta **app/views/comments/** ( en la misma ubicación que el archivo create.js.erb ).

```erb
$('#comments_<%= @post.id %>').html("<%= j render @post.comments, post: @post, comment: @comment %>");
```

## Resources

Aquí están algunos recursos utiles para poder seguir aprediendo.
Algunos sirvieron también en la elaboración de esta guía.

*Introducción a Rails - codigofacilito* [http://rubysur.org/introduccion.a.rails/](https://codigofacilito.com/articulos/mvc-model-view-controller-explicado)

*MVC (Model, View, Controller) Explicado - codigofacilito:* [https://codigofacilito.com/articulos/mvc-model-view-controller-explicado](https://codigofacilito.co/articulos/mvc-model-view-controller-explicado)

*Asociaciones - Make it Real:* [https://makeitrealcamp.gitbook.io/ruby-on-rails-5/asociaciones](https://codigofacilito.com/articulos/mvc-model-view-controlle-explicado)

*Make it Real - Ruby on Rails:* [https://guias.makeitreal.camp/ruby-on-rails-i](https://guias.makeitreal.camp/ruby-on-rails-i)

*Ruby on Rails: El desarrollo web que no molesta:* [http://rubyonrails.org.es/](http://rubyonrails.org.es/)

*Introducción a Ruby on Rails:* [https://uniwebsidad.com/libros/introduccion-rails](https://uniwebsidad.com/libros/introduccion-rails)

*Tutorial de Ruby on Rails (3a. edición.) - Michael Hartl* [https://spanish.railstutorial.org/book](https://spanish.railstutorial.org/book)


## Debug

Error para correr `rails console`

`Library not loaded: /usr/local/opt/readline/lib/libreadline.7.dylib (LoadError)`

https://gist.github.com/zulhfreelancer/47efc39584cb9f006da43c41c014e03a
