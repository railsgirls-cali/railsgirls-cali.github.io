---
layout: inner
title: Instagram - Rails 6
lead_text: Crea un clon de Instagram desde cero
permalink: /instagram-r7/
---

### Repositorio de la aplicación

[https://github.com/railsgirls-cali/instagram-2023](https://github.com/railsgirls-cali/instagram-2023)


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

## 0. interactuando con Cloud9 - Instalemos lo necesario...

Para evitar instalar programas en tu computador, hemos seleccionado esta plataforma que ofrece Amazon AWS y se ejecuta en una explorador web, te provee un entorno completo de trabajo:

1. Computador virtual en la nube de AWS
2. Terminal de comandos
3. Editor de código (editor de texto)
4. Explorador web

Dile a tu coach que te recuerde cómo usar Cloud9...

Ahora bien, dentro de la terminal de Cloud9 debes digitar el siguiente comando:

`consola`

```bash
cd
```

y luego vamos a crear una nueva carpeta, recuerda que a final de cuentas, una terminal es una interfz de usuario, pero en lugar de usar el ratón para interactuar con los archivos y carpetas, usamos el teclado, muy retro no...?

`consola`

```bash
mkdir aplicaciones
```

aquí estamos creando la carpeta `aplicaciones` y es la carpeta que vamos a usar dentro de nuestro computador virtual para almacenar todo el código de nuestra aplicación.

Esta será una de las pocas palabras que usaremos en español... a Ruby on Rails le gusta más que usemos el inglés :)

Muy bien, ahora vamos a proceder a instalar la versión 2.7.7 del lenguaje de programación Ruby, es la versión más reciente con la que es compatible Cloud9, sin embargo, no es la versión más reciente del lenguaje...

Para hacerlo, digitamos el siguiente comando:

`consola`

```bash
rvm install 2.7.7
```

`rvm` es un programa que ya viene pre-instalado en Cloud9 con el cual podemos instalar diferentes versiones de Ruby, al final del proceso vamos a ver algo como esto:

```bash
ruby-2.7.7 - #extracting ruby-2.7.7 to /home/ec2-user/.rvm/src/ruby-2.7.7.....
ruby-2.7.7 - #configuring.............................................................
ruby-2.7.7 - #post-configuration..
ruby-2.7.7 - #compiling............................................................................................
ruby-2.7.7 - #installing................................
ruby-2.7.7 - #making binaries executable...
Installed rubygems 3.1.6 is newer than 3.0.9 provided with installed ruby, skipping installation, use --force to force installation.
ruby-2.7.7 - #gemset created /home/ec2-user/.rvm/gems/ruby-2.7.7@global
ruby-2.7.7 - #importing gemset /home/ec2-user/.rvm/gemsets/global.gems................................................................
ruby-2.7.7 - #generating global wrappers.......
ruby-2.7.7 - #gemset created /home/ec2-user/.rvm/gems/ruby-2.7.7
ruby-2.7.7 - #importing gemsetfile /home/ec2-user/.rvm/gemsets/default.gems evaluated to empty gem list
ruby-2.7.7 - #generating default wrappers.......
ruby-2.7.7 - #adjusting #shebangs for (gem irb erb ri rdoc testrb rake).
Install of ruby-2.7.7 - #complete 
Ruby was built without documentation, to build it run: rvm docs generate-ri
```

Para terminar este paso, debemos ahora decirle a `rvm` que la version que vamos a usar por defecto será siempre la versión de RUby 2.7.7. digitando este comando:

`consola`

```bash
rvm default 2.7.7
```

Luego procederemos a instalar la ultima versión de Ruby on Rails, recuerda Ruby es el lenguaje, y Rails es un Framework que usa a Ruby para poder construir aplicaciones web asombrosas

Para hacerlo digita el siguiente comando, la opción --no-document evitará instalar la documentación, sólo por esta vez lo haremos así, para hacer la instalación más ligera:


`consola`

```
gem install rails --no-document
```

al final deberas ver algo como:

```
Successfully installed rails-7.0.4.2
37 gems installed
```

la versión de Rails que estaremos usando es **Rails 7.0.4**

Ahor vamos a instalar un par de herramientas que son necesarias como complemento de Rails en el entorno de Cloud9

1. YARN, en la console ejecutaremos lo siguiente:

`consola`

```
npm install -g yarn
```

2. ESBUILD, en la console ejecutaremos lo siguiente:

`consola`

```
curl -fsSL https://esbuild.github.io/dl/v0.17.5 | sh
```

y luego

```
sudo mv esbuild /usr/bin/
```

3. SASS, en la console ejecutaremos lo siguiente:

`consola`

```
npm install -g sass
```

Por último dile a tu coach que modifique los siguientes parámetros del editor:

1. Soft Tabs en **2** en el Porject Settings
2. Auto Save en **on-focus** en Experimental

## 1. Crea una aplicación nueva

### ¡Vamos a crear  una nueva aplicación basada en Instagram!

En la consola, y dentro de la carpeta `aplicaciones`, escribímos

`consola`

```bash
rails new instagram -j esbuild --css bootstrap
```

Despues de este comando presiona enter y se va a crear una serie de archivos y dependencias organizados en carpetas que conforman la estructura de una aplicación Rails, la carpeta principal tendrá el mismo nombre de la aplcación en este caso sera: **instagram**

Una vez terminado puedes ver la ultima linea que dice (la cantidad de sgundos puede variar):

```
✨  Done in 1.56s.
```

Después de crear la aplicación, entra a su directorio para continuar trabajando directamente en ella:

En la consola

```
cd instagram
```

En este punto, vamos a declarar la carpeta como favorito en el editor de Cloud9, pidele ayuda a tu coach para hacer esta parte, la idea es que el ábrol de directorios sólo veas la carpeta `instagram`

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
=> Rails 7.0.4.2 application starting in development 
=> Run `bin/rails server --help` for more startup options
Puma starting in single mode...
* Puma version: 5.6.5 (ruby 2.7.7-p221) ("Birdie's Version")
*  Min threads: 5
*  Max threads: 5
*  Environment: development
*          PID: 29530
* Listening on http://127.0.0.1:8080
* Listening on http://[::1]:8080
Use Ctrl-C to stop
```

Que significa que nuestra aplicacion ya esta corriendo en el navegador.

En el navegador, ve a la URL: http://localhost:8080 Esta es la página de inicio por defecto para las aplicaciones Rails.

Pero para verla usando Cloud9 debes usar el proxy de Cloud9, dado que estás usando un computador virtual en la nube, no vas a poder acceder directamente a un explorador, y es por esa razón que debemos usar el proxy que Cloud9 nos provee.

Para previsualizar nuestra aplicación debemos ir a nuestra pataforma en Cloud9, dar clic en **Preview** de la parte superior, y luego clic en **preview running application**, allí una nueva pestaña se te abrirá y para maor comodida te recomiendo que debes copiar la URL completa para llevarla a una pestaña de tu explorador web (en el que estás trabajando), la URL se debe ver similar a esta `https://716cb3ec2b8244ffada0813ea864deb0.vfs.cloud9.us-east-1.amazonaws.com/`

**NOTA** si estás usando safari, es importante que habilites el uso de cookies, o puedes igualmente iniciar sesión en otro explorador, la guía fue probada en Google Chrome.

Una vez hayas abierto esta pestaña, veras un error en color rojo, hey! es normal, no te asustes ;) es sólo un sistema de seguridad de Rails que usa para evitar que tu aplicación sea usada en dominios no autorizados.

para corregir este error deberas copiar la siguiente línea:

```
config.hosts << /[a-z0-9]+\.vfs\.cloud9\..*\.amazonaws\.com/
```

en el archivo `config/environments/development.rb` justo después de la línea `Rails.application.configure do` algo así:
```
Rails.application.configure do
  config.hosts << /[a-z0-9]+\.vfs\.cloud9\..*\.amazonaws\.com/
  # Settings specified here will take precedence over those in config/application.rb.
```

una vez añadida esta línea, deberas guardar el archivo, y reiniciar el servidor que esta corriendo en la temrinal:

CONTROL + C (para parar el servidor)

`consola`

```bash
rails server # (para volver a iniciar el servidor)
```

La página "Rails!" es la primera prueba para una nueva aplicación Rails. Ésta asegura que tienes el software configurado correctamente para servir una página.


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

**NOTA** El primer tab de tu consola ya tiene el servidor de Rails corriendo que lanzaste con el comando:

```
rails server
```

Para crear un nuevo controlador, debes crear una nueva pestaña en la consola y necesitas ejecutar el generador de controladores y decirle que quieres un controlador llamado por ejemplo `pages` con una acción llamada `home`. Para ello, ejecuta lo siguiente:

**recuerda abrir un nuevo tab.**

En la consola aparecerá un nuevo prompt `$ ` donde puedes ejecutar:

```
rails generate controller pages home
```

Rails creará una serie de archivos y añadirá una ruta hacia la página por ti.

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
```

Estas convenciones que estabamos hablando un poco más arriba son las que permiten definir lo que se va a crear cada vez que ejecutemos un comando de Rails. Podríamos tambien crear los archivos manualmente y escribir el codigo, pero Rails se encarga de crear el esqueleto o la estrucutra base para ahorarnos tiempo e implementar buenas prácticas basadas en la experiencia colectiva de los desarolladores que contribuyen en proyectos de codigo abiertos como Ruby on Rails.

Los archivos más importantes que acabamos de crear con el generador son por supuesto el controlador, que se encuentra en **app/controllers/pages_controller.rb** y la vista (HTML), que se encuentra en **app/views/pages/home.html.erb**.

Miremos un poco acerca de la convencion que sigue estos archivos.
La mayoría del trabajo en esta guia se llevará a cabo en la carpeta **app/**, y vemos que el primer archivo, el controlador, se creo en una carpeta que se llama `controllers`, se llama `pages_controller.rb` y tiene una accion llamada `home`.

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
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  # Defines the root path route ("/")
  # root "articles#index"
end
```

**NOTA** El algunos archivos puedes ver un texto que impieza con el numeral `#`. Este texto hace parte de los **comentarios** (usado como oraciones para documentar el código, y normalmente no afectan en nada al código) que se estan autogenerando que dan algunas indicaciones a a el usuarios de como seguir la convenciones de Rails.


### Actualiza el texto en la nueva página

Ahora actualizaremos el archivo de inicio.
Abre el archivo **app/views/pages/home.html.erb** en tu editor de texto y edítalo para que contenga sólo está línea de código:

```html
<h1>¡Bienvenidos a Instagram!</h1>
```

En tu navegador, ve a la URL : /pages/home y ve la nueva página que se acaba de crear.


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

Este pequeño cambio indica a Rails que en la pagina de inicio de nuestra aplicación ubicada enla direccion web [/] queremos mostrar la pagina `home`.


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

- [/]: la pagina de inicio
- [/about]: la pagina donde encontrar información sobre ti en tu proyecto.


## 5. ¡Entendiendo Bootstrap!

Los desarrolladores de aplicaciones web pueden trabajar programando la lógica de la aplicación y programando la interfaz gráfica del usuario final, esta última parte es mucho más estética, y para facilitar la diagramación y el diseño de componentes gráficos usamos herramientas como Bootstrap, dile a tu coach que te acompañe en una revisión rápida de esta tecnología [aquí](https://getbootstrap.com/docs/5.3/getting-started/introduction/)

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
  <br>
  <%= yield %>
</div>
```

**NOTA** ten cuidado con la indentación del código que copias y pegas, la legibilidad del código es muy importante para que no te confundas.

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

**app/assets/stylesheets/application.bootstrap.scss**

Reemplaza:

```scss
@import 'bootstrap/scss/bootstrap';
@import 'bootstrap-icons/font/bootstrap-icons';
```

por los siguientes estilos:

```scss
@import url(http://fonts.googleapis.com/css?family=Lato:400,700);
@import url(http://fonts.googleapis.com/css?family=Oleo+Script);

$font-family-sans-serif:           'Lato', 'Helvetica Neue', Helvetica, Arial, sans-serif;
$primary:                          #d3252c;
$jumbotron-bg:                     white;

@import 'bootstrap/scss/bootstrap';
@import 'bootstrap-icons/font/bootstrap-icons';

.navbar {
  background-color: #fff;
  font-weight: bold;
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

Debajo de `gem "bootsnap", require: false` añade la gema de Devise.


```ruby
[...]
gem 'devise'
[...]
```

Ahora vamos a la pestaña en la que está corriendo el servidor `rails server`, detenemos el servidor y procedemos a instalar la biblioteca añadida.

### Siempre pare el servidor con `CONTROL + C` y corre `bundle install` para instalar una nueva gema

Ejecuta `bundle install` para instalarla

**CONTROL + C**

`consola`

```bash
bundle install
```

### Vuelve a iniciar el servidor

**NOTA** pero esta vez no vamos a usar `rails server` ahora vamos a usar `bin/dev` la razón de usar este comando es porque nos facilitará el proceso de creación de todos los archivos necesarios para nuestra aplicación, antes sólo estabamos corriendo el servidor que permite ejecutar el código Ruby que hemos hecho hasta ahora, pero con el nuevo comando `bin/dev` no sólo ejecutaremos código Ruby, sino también le permitiremos a nuestra ejecución interpretar de algún modo JS (javascript) y (SCSS/CSS), que por el momento diremos que son tecnologías que nos permiten volver nuestra aplicación web (la que ves desde el explorador) más bonita e interactiva. Así que al correr el comando `bin/dev` estás corriendo implicitamente el servidor, y otros dos procesos más en una misma consola, además vas a notar cambios importantes en la interfaz gráfica, cambios que tu está generando pero que ahora los podrás ver de forma automática.

De igual forma, en Cloud9 el puerto que se está usando para ejecutar es el 8080, normalmente usa el puerto 3000, para configurar esto en el comando `bin/dev` debemos editar el archivo `Procfile.dev` que está en la raíz del proyecto, cambia su contenido completo por el siguiente contenido:

```
web: unset PORT && bin/rails server -p 8080
js: yarn build --watch
css: yarn build:css --watch
```

`consola`

```bash
bin/dev
```

al ejecutarlo, veras algo como lo siguiente:

```bash
22:06:30 css.1  | $ sass ./app/assets/stylesheets/application.bootstrap.scss:./app/assets/builds/application.css --no-source-map --load-path=node_modules --watch
22:06:30 js.1   | $ esbuild app/javascript/*.* --bundle --sourcemap --outdir=app/assets/builds --public-path=assets --watch
22:06:31 js.1   | [watch] build finished, watching for changes...
22:06:31 web.1  | => Booting Puma
22:06:31 web.1  | => Rails 7.0.4.2 application starting in development 
22:06:31 web.1  | => Run `bin/rails server --help` for more startup options
22:06:32 web.1  | Puma starting in single mode...
22:06:32 web.1  | * Puma version: 5.6.5 (ruby 2.7.7-p221) ("Birdie's Version")
22:06:32 web.1  | *  Min threads: 5
22:06:32 web.1  | *  Max threads: 5
22:06:32 web.1  | *  Environment: development
22:06:32 web.1  | *          PID: 10225
22:06:32 web.1  | * Listening on http://127.0.0.1:8080
22:06:32 web.1  | * Listening on http://[::1]:8080
22:06:32 web.1  | Use Ctrl-C to stop
22:06:37 css.1  | Compiled app/assets/stylesheets/application.bootstrap.scss to app/assets/builds/application.css.
22:06:37 css.1  | Sass is watching for changes. Press Ctrl-C to stop.
22:06:37 css.1  | 
```

## 10. Configuración de Devise

**NOTA** El primer tab de tu consola todavía tiene el servidor de Rails corriendo.
Sigue usando el otro tab / pestaña.


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

Ve a **db/migrate** y deberías tener en los archivos algo así como **db/migrate/20230218222747_devise_create_users.rb**

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

CONTROL + C (para parar el servidor)

`consola`

```bash
rails server # (para volver a iniciar el servidor)
```

Tendrás que reiniciar la aplicación cada vez que **instales una gema** o cada vez que ejecutes `rails db:migrate`



## 11. Mensajes flash e I18n

Los mensajes flash son los mensajes en sitios web que dicen "Gracias por registrarse en ..." o "Gracias por suscribirse a ..."

**app/views/layouts/application.html.erb**

Agrega lo siguiente Debajo de `<div class="container">` y antes de `<br>`:

```rhtml
<% flash.each do |name, msg| %>
  <% if msg.is_a?(String) %>
    <div class="alert alert-<%= name.to_s == 'notice' ? 'success' : 'danger' %> alert-dismissible fade show text-center">
      <%= msg %>
    </div>
  <% end %>
<% end %>
```

### I18n Internacionalización

Ahora vamos a complementar nuestra aplicación con un sistema básico de traducción estática, normalmente, Rails usa Inglés como su lenguaje base, pero existe una gema que nos permitirá usar el lenguaje español en los términos donde usualmente usa inglés.

Así que para instalar esta gema, debes ir al Gemfile y justo despues de la línea `# gem "image_processing", "~> 1.2"` debes colocar `gem 'rails-i18n'` al final deberá quedarte así:

```
# gem "image_processing", "~> 1.2"

# I18n
gem 'rails-i18n'
```

Ahora le diremos a nuestra aplicación que acepte los lenguajes español : es, e ingles : en, esto lo hacemos en el archivo `config/application.rb`. Dentro de ese archivo y justo después de la línea `config.load_defaults 7.0` debemos colocar lo siguiente:

```
config.i18n.available_locales = %w[es en]
```

y luego debemos ir a nuestro controlador principal `app/controllers/application_controller.rb` y cambiar todo su contenido por el siguiente:

```
class ApplicationController < ActionController::Base
  before_action :i18n_setup

  protected

  def i18n_setup
    I18n.locale = 'es'
  end
end
```

Con lo anterior siempre estaremos forzando ek lenguaje español en cada petición/ejecución.

Ahora, ve a la consola donde está corriendo el servidor...

CONTROL + C (para parar el servidor)

`consola`

luego instala la gema usando:

```bash
bundle install
```

y despues...

```bash
bin/dev # (para volver a iniciar el servidor)
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
<nav class="navbar navbar-expand-lg bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Rails Girls Cali</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <%= link_to "Home", root_path, class: "nav-link" %>
        </li>
        <li class="nav-item">
          <%= link_to "Quiénes somos", about_path, class: "nav-link" %>
        </li>
        <% if user_signed_in? %>
          <li class="nav-item">
            <%= link_to "Cerrar sesión", destroy_user_session_path, class: "nav-link", data: { turbo_method: :delete } %>
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
    </div>
  </div>
</nav>
```

**NOTA** Usa el tabulador, la tecla Tab (Tab ↹) nos permite indentar el texto que este en nuestra selección y así mantener el código organizado y indentado.


## 13. Cambia las vistas de Devise

Cuando corrimos el comando `rails g devise:views` el generador creo un serie de vistas con formularios responsable del registro de usuario, el inicio de sesion etc.
Todos estas vistas están ubicadas dentro de la carpeta **app/views/devise**.
Ahora vamos a mejorar un poco estos archvos agregando CSS de Bootstrap.


### Reemplaza el código completo  para cada una de las vistas de Devise

**app/views/devise/registrations/new.html.erb**

*Esta vista se encarga del formulario de registro de usuarios en tu app.*

```rhtml
<div class="form-wrapper container">
  <div class="row justify-content-md-center mt-3">
    <div class="col-lg-6">
      <h1>Regístrate</h1>

      <%= form_for(resource, as: resource_name, url: registration_path(resource_name), data: { turbo: false }) do |f| %>
        <%= render "devise/shared/error_messages", resource: resource %>

        <div class="form-group">
          <%= f.label :email %>
          <%= f.email_field :email, autofocus: true, class: "form-control" %>
        </div>

        <div class="form-group mt-3">
          <%= f.label :password %>
          <%= f.password_field :password, class: "form-control" %>
        </div>

        <div class="form-group mt-3">
          <%= f.submit "Regístrate", class: "btn btn-success" %>
        </div>
      <% end %>

      <div class="form-group text-center">
        <%= render "devise/shared/links" %>
      </div>
    </div>
  </div>
</div>
```

**app/views/devise/registrations/edit.html.erb**

*Esta vista se encarga del formulario de edición de la información de usuarios en tu app.*

```rhtml
<div class="form-wrapper container">
  <div class="row justify-content-md-center mt-3">
    <div class="col-lg-6">
      <h1>Editar <%= resource_name.to_s.humanize %></h1>

      <%= form_for(resource, :as => resource_name, url: registration_path(resource_name), data: { turbo: false }, html: { method: :put }) do |f| %>
        <%= render "devise/shared/error_messages", resource: resource %>

        <div class="form-group">
          <%= f.label :email %>
          <%= f.email_field :email, class: "form-control", autofocus: true %>
        </div>

        <div class="form-group mt-3">
          <%= f.label :password %> <i>(déjala en blanco si no quieres cambiarla)</i>
          <%= f.password_field :password, class: "form-control", autocomplete: "off" %>
        </div>

        <div class="form-group mt-3">
          <%= f.label :current_password %> <i>(necesitamos tu contraseña actual para confirmar los cambios)</i>
          <%= f.password_field :current_password, class: "form-control" %>
        </div>

        <div class="form-group mt-3">
          <%= f.submit "Actualizar", class: "btn btn-success" %>
        </div>
      <% end %>

      <h3>Cancelar mi cuenta</h3>

      <p>Unhappy? <%= button_to "Cancelar mi cuenta", registration_path(resource_name), data: { confirm: "¿Estás segura/o?" }, method: :delete, class: "btn btn-warning" %></p>

      <%= link_to "Volver", :back %>
    </div>
  </div>
</div>

```

**app/views/devise/passwords/new.html.erb**

*Esta vista está encargada de mostrar el formulario para la solicitud de contraseña al sistema en caso de olvido.*

```rhtml
<div class="form-wrapper container">
  <div class="row justify-content-md-center mt-3">
    <div class="col-lg-6">
      <h1>¿Olvidaste tu contraseña?</h1>

      <%= form_for(resource, as: resource_name, url: password_path(resource_name), data: { turbo: false }, html: { method: :post }) do |f| %>
        <%= render "devise/shared/error_messages", resource: resource %>

        <div class="form-group">
          <%= f.label :email %>
          <%= f.email_field :email, class: "form-control", autofocus: true %>
        </div>

        <div class="form-group mt-3 d-grid">
          <%= f.submit "Envíame las instrucciones para restablecer mi contraseña", class: "btn btn-block btn-success" %>
        </div>
      <% end %>

      <div class="form-group text-center">
        <%= render "devise/shared/links" %>
      </div>
    </div>
  </div>
</div>
```

**app/views/devise/passwords/edit.html.erb**

*En esta vista se encuentra el formulario para el cambio de la contraseña de un usuario de tu app*

```rhtml
<div class="form-wrapper container">
  <div class="row justify-content-md-center mt-3">
    <div class="col-lg-6">
      <h1>Cambia tu contraseña</h1>

      <%= form_for(resource, as: resource_name, url: password_path(resource_name), data: { turbo: false }, html: { method: :put }) do |f| %>
        <%= render "devise/shared/error_messages", resource: resource %>
        <%= f.hidden_field :reset_password_token %>

        <div class="form-group">
          <%= f.label :password, "Nueva contraseña" %>
          <%= f.password_field :password, class: "form-control", autofocus: true %>
        </div>

        <div class="form-group mt-3">
          <%= f.label :password_confirmation, "Confirmar nueva contraseña" %>
          <%= f.password_field :password_confirmation %>
        </div>

        <div class="form-group mt-3">
          <%= f.submit "Cambiar mi contraseña", class: "btn btn-success" %>
        </div>
      <% end %>

      <div class="form-group text-center">
        <%= render "devise/shared/links" %>
      </div>
    </div>
  </div>
</div>
```

**app/views/devise/sessions/new.html.erb**

*¡Este es el formulario de login (inicio de sesión) de tu Instagram app!*

```rhtml
<div class="form-wrapper container">
  <div class="row justify-content-md-center mt-3">
    <div class="col-lg-6">
      <h1>Iniciar Sesion</h1>
      <%= form_for(resource, :as => resource_name, :url => session_path(resource_name), data: { turbo: false }) do |f| %>
        <div class="form-group">
          <%= f.label :email %>
          <%= f.email_field :email, class: "form-control", autofocus: true %>
        </div>

        <div class="form-group mt-3">
          <%= f.label :password %>
          <%= f.password_field :password, class: "form-control" %>
        </div>

        <div class="checkbox">
          <%= f.check_box :remember_me %>
          <%= f.label :remember_me %>
        </div>

        <div class="form-group mt-3">
          <%= f.submit "Ingresa", class: "btn btn-success" %>
        </div>
      <% end %>

      <div class="form-group text-center">
        <%= render "devise/shared/links" %>
      </div>
    </div>
  </div>
</div>
```

**app/views/devise/shared/_error_messges_.html.erb**

*¡Esta es la vista respecto de cómo se visualizan los errores!*

```
<% if resource.errors.any? %>
  <div id="error_explanation">
    <h2>
      Los siguientes errores están presentes:
    </h2>
    <ul>
      <% resource.errors.full_messages.each do |message| %>
        <li><%= message %></li>
      <% end %>
    </ul>
  </div>
<% end %>
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


## 15. Modifiquemos el controlador de Posts

**app/controllers/posts_controller.rb**

### Reemplaza todo el contenido del controlador

```ruby
class PostsController < ApplicationController
  before_action :set_post, only: %i[ show edit update destroy ]

  # GET /posts or /posts.json
  def index
    @posts = Post.all
  end

  # GET /posts/1 or /posts/1.json
  def show
  end

  # GET /posts/new
  def new
    @post = Post.new
  end

  # GET /posts/1/edit
  def edit
  end

  # POST /posts or /posts.json
  def create
    @post = Post.new(post_params)

    respond_to do |format|
      if @post.save
        format.html { redirect_to post_url(@post), notice: "El post fue exitosamente creado." }
        format.json { render :show, status: :created, location: @post }
      else
        format.html { render :new, status: :unprocessable_entity }
        format.json { render json: @post.errors, status: :unprocessable_entity }
      end
    end
  end

  # PATCH/PUT /posts/1 or /posts/1.json
  def update
    respond_to do |format|
      if @post.update(post_params)
        format.html { redirect_to post_url(@post), notice: "El post fue exitosamente actualizado." }
        format.json { render :show, status: :ok, location: @post }
      else
        format.html { render :edit, status: :unprocessable_entity }
        format.json { render json: @post.errors, status: :unprocessable_entity }
      end
    end
  end

  # DELETE /posts/1 or /posts/1.json
  def destroy
    @post.destroy

    respond_to do |format|
      format.html { redirect_to posts_url, notice: "El post fue exitosamente eliminado." }
      format.json { head :no_content }
    end
  end

  private
    # Use callbacks to share common setup or constraints between actions.
    def set_post
      @post = Post.find(params[:id])
    end

    # Only allow a list of trusted parameters through.
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
<%= form_with(model: post) do |form| %>
  <% if post.errors.any? %>
    <div style="color: red">
      <h2><%= pluralize(post.errors.count, "error") %> están evitando que el post sea guardado:</h2>

      <ul>
        <% post.errors.each do |error| %>
          <li><%= error.full_message %></li>
        <% end %>
      </ul>
    </div>
  <% end %>

  <div class="form-group">
    <%= form.label :description %>
    <%= form.text_field :description, class: "form-control" %>
  </div>

  <div class="form-group mt-3">
    <%= form.submit class: "btn btn-primary" %>
  </div>
<% end %>
```

### Para mantener nuestros estilos, tendremos el contenido de las siguientes vistas dentro de un form-wrapper

Cambia todo lo que hay en este archivos: **app/views/posts/new.html.erb** por:

```rhtml
<div class="form-wrapper">
  <h2>Crear un post</h2>
  <%= render "form", post: @post %>
</div>

<div>
  <%= link_to "Back to posts", posts_path %>
</div>
```

Y lo que hay en este archivo **app/views/posts/edit.html.erb** por

```rhtml
<div class="form-wrapper">
  <h2>Actualizar un post</h2>
  <%= render "form", post: @post %>
</div>

<div class="text-center edit-links">
  <%= link_to "Mirá este post", @post %> |
  <%= link_to "Eliminar este Post", post_path(@post), data: { turbo_method: :delete, turbo_confirm: "¿Estás segura que quieres eliminar este post?" } %> |
  <%= link_to "Lista de posts", posts_path %>
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


## 17. Posts, Usuarios, Asociaciones y Validaciones

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
class Post < ApplicationRecord
  belongs_to :user
end
```

### Genera una nueva migración de índice de un usuario

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

TODO: * ##### Cada vez que hagas una migración, debes reiniciar el servidor de Rails.

`consola`

CONTROL + C (para parar el servidor)

```bash
bin/dev # (para volver a iniciar el servidor)
```


### Un Usuario `has_many` Posts

##### Un Usuario ***tiene*** muchas Publicaciones

En el modelo `User` **app/models/user.rb** remplaza el contenido por:

```ruby
class User < ApplicationRecord
  # Include default devise modules. Others available are:
  # :confirmable, :lockable, :timeoutable, :trackable and :omniauthable
  devise :database_authenticatable, :registerable,
         :recoverable, :rememberable, :validatable

  has_many :posts
end
```

### Validaciones

Para evitar que un Post pueda ser guardado sin descripción, podemos usar la validaciones de Ruby on Rails, para usarlas añade al archivo `models/post.rb` la línea `validates :description, presence: true` justo después de la línea `belongs_to :user`. Quedando finalmente el archivo `post.rb` así:

```ruby
class Post < ApplicationRecord
  belongs_to :user
  validates :description, presence: true
end
```

**NOTA:** intenta interactuar hasta este punto con la aplicación, creando o editando Posts, es posible que te encuentres con algunos errores, los abordaremos más adelante :)

## 18. Autorización: ¿Quién puede? ¿Quién no puede?

Una vez que un usuario tiene acceso a la plataforma, hay que ver los permisos que este usuario tiene.

- Tenemos que asegurar que un usuario no puede cambiar la publicación de otro usuario.

- También que las acciones (crear, cambiar o borrar una publicación) se puede hacer solamente si estas autenticado.


### Actualiza el controlador Posts

Ahora vamos a cambiar el codigo para que un usuario pueda crear, editar y borrar sus publicaciones y no aceder a todas.

**app/controllers/posts_controller.rb**

```ruby
class PostsController < ApplicationController
  before_action :set_post, only: %i[ show edit update destroy ]

  # GET /posts or /posts.json
  def index
    @posts = Post.all
  end

  # GET /posts/1 or /posts/1.json
  def show
  end

  # GET /posts/new
  def new
    @post = current_user.posts.build
  end

  # GET /posts/1/edit
  def edit
  end

  # POST /posts or /posts.json
  def create
    @post = current_user.posts.build(post_params)

    respond_to do |format|
      if @post.save
        format.html { redirect_to post_url(@post), notice: "El post fue exitosamente creado." }
        format.json { render :show, status: :created, location: @post }
      else
        format.html { render :new, status: :unprocessable_entity }
        format.json { render json: @post.errors, status: :unprocessable_entity }
      end
    end
  end

  # PATCH/PUT /posts/1 or /posts/1.json
  def update
    respond_to do |format|
      if @post.update(post_params)
        format.html { redirect_to post_url(@post), notice: "El post fue exitosamente actualizado." }
        format.json { render :show, status: :ok, location: @post }
      else
        format.html { render :edit, status: :unprocessable_entity }
        format.json { render json: @post.errors, status: :unprocessable_entity }
      end
    end
  end

  # DELETE /posts/1 or /posts/1.json
  def destroy
    @post.destroy

    respond_to do |format|
      format.html { redirect_to posts_url, notice: "El post fue exitosamente eliminado." }
      format.json { head :no_content }
    end
  end

  private
    # Use callbacks to share common setup or constraints between actions.
    def set_post
      @post = Post.find(params[:id])
    end

    def correct_user
      @post = current_user.posts.find_by(id: params[:id])
      redirect_to posts_path, notice: "¡No tienes permisos para editar este post!" if @post.nil?
    end

    # Only allow a list of trusted parameters through.
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
before_action :authenticate_user!, except: %i[index show]
```

### Añade el `:correct_user`

Añade el método `before_action` a tu controlador de Posts

**app/controllers/posts_controller.rb**

Debajo de `before_action :authenticate_user! ...`

```ruby
before_action :correct_user, only: %i[edit update destroy]
```

### Experimentar con usuarios

Con tu coach trata de crear nuevos usuarios y posts, luego trata de editar la información de los posts con diferentes usuarios.

**NOTA** sólo si ves este error `undefined method `user_url' for #<Devise::RegistrationsController:0x0000000000....>` comunicate con tu coach, el problema es debido a una incompatibilidad de redireccionamiento entre Devise y un sistema interno de Ruby on Rails llamado Turbo.

la solución es sencilla, sólo debes añadir la siguiente línea de código al bloque de configuración del archivo `config/initializers/devise.rb`

```ruby
config.navigational_formats = ['*/*', :html, :turbo_stream]
```

Tu coach puede ver más información al respecto [aquí](https://github.com/heartcombo/devise/issues/5439)


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

### Instalando ImageMagick

Para poder lidiar con imágenes, es bueno tener un editor de imágenes, algo como Photoshop pero en consola (just kiding), por el momento usaremos ImageMagick, y debemos instalarlo, como estamos trabajando con Cloud9 preferiremos usar ImageMagick en lugar de VIPS que por rendimiento es más recomendado.

para instalarlo, en una consola debes digitar el siguiente comando, y aceptar la instalación, dile a tu coach que supervise esta instalación:

`consola`

```bash
sudo yum install ImageMagick
```

### Instalar image_processing

Ahora necesitamos instalar un libreria para procesar nuestras imagenes con las caracteriticas y el tamaño de las imagenes que se suben a Instagram, entonces agregaremos la gema `image_processing`.


Dentro del archivo **/gemfile** busca la linea `gem 'image_processing', '~> 1.2'` y quitale el `#` para que se vea de la siguiente forma:

```ruby
# Use Active Storage variant
gem "image_processing", "~> 1.2"
```

Acabamos simplemente de remover un character que significa que esta linea es un comentario.
Ahora esta linea es parte del codigo y podemos ejecutar `bundle install` para instalar esta nueva gema.

`consola`

CONTROL + C (para parar el servidor)

```bash
bundle install
```

Y despues


```bash
bin/dev
```

Para iniciar el servidor otra vez.

### Actualiza Post

Actualiza el model `Post`

**/app/models/post.rb**

```ruby
class Post < ApplicationRecord
  belongs_to :user
  validates :description, presence: true

  has_one_attached :image

  def user_name
    user.email
  end

  def squared_img
    return 'https://via.placeholder.com/600' unless image.attached?

    image.variant(resize_to_fill: [600, 600])
  end
end
```

Aquí hemos añadido dos nuevos métodos `user_name` `squared_img`, qué crees que hacen esos dos métodos? discútelo con tu coach...

para parender más del redimensionamiento de imágenes ver [aquí](https://dev.to/mikerogers0/resize-images-with-active-storage-in-rails-481n)

Finalmente, para forzar a Rails usar ImageMagick y no VIPS, debemos añadir esta línea `config.active_storage.variant_processor = :mini_magick` justo después de la línea `config.active_storage.service = :local` en el siguiente archivo `config/environments/development.rb`

### Edita el formulario de Post

**/app/views/posts/_form.html.erb**

Justo despues de

```rhtml
<div class="form-group">
  <%= form.label :description %>
  <%= form.text_field :description, class: "form-control" %>
</div>
```

Añade:

```rhtml
  <div class="form-group mt-3">
    <%= form.label :image %>
    <%= form.file_field :image %>
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
  <div class="main-wrapper posts">
    <div class="row">
      <% @posts.each do |post| %>
        <div class="col-xs-12 col-sm-6 col-md-4">
          <div class="image center-block">
            <%= link_to (image_tag post.squared_img, class:'img-fluid'), post_path(post) %>
          </div>
          <p class="text-end small text-muted mb-0">
            <%= time_ago_in_words post.created_at %>
          </p>
          <p class="description">
            <b>
              <%= post.user_name if post.user %>
            </b>
            <%= truncate(strip_tags(post.description.to_s), length: 70) %>
          </p>
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

**/app/views/posts/_post.html.erb**

```rhtml
<div id="<%= dom_id post %>" class="posts-wrapper row">
  <div class="post">
    <div class="image center-block">
      <%= image_tag post.squared_img, class:'img-responsive' %>
    </div>
    <div class="post-head">
      <div class="name">
        <%= post.user.email if post.user %>
      </div>
    </div>
    <p class="description">
      <%= post.description %>
    </p>
  </div>
</div>
```

### Con el estilo Instagram

Ahora vamos a colocar más bonito nuestra aplicación especialmente cuando un Post es presentado

Vamos a crear el archivo `app/assets/stylesheets/post.css.scss` con el siguiente contenido:

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
  text-align: center;
  padding-top: 20px;
}

.description {
  padding: 24px 24px;
  font-size: 15px;
  line-height: 18px;
}
```

En este caso, nos estamos saliendo del archivo principal de estilos, esto es una decisión comun dentro del desarrollo de software para no tener un súper archivo lleno de muchas líneas de código... lo que hacemos es dividir ese archivo en partes que tengan más sentido (divide y venceras)m y en este caso hemos creado otro archivo de estilo sólo para volver más bonitos los posts.

Sin embargo, en Ruby on Rails, debemos una sola vez hacer tres pasos más cuando tomamos esta decisión:

1. enlazar el nuevo "asset" creado llamado `post.css.scss`, para esto vamos a reemplazar el contenido completo del archivo `app/assets/config/manifest.js` por:

```js
//= link_tree ../images
//= link_tree ../builds
//= link post.css
```

Aquí pueden notar que usamos `post.css` en lugar de `post.css.scss` esto es porque al final del día un explorador web sólo entiende CSS, JS y HTML, y SCSS (o SASS) sólo lo usamos para poder escribir los estilos mucho más rápido, SCSS es entonces un meta-lenguaje que nos ayuda a escribir de forma más ordenada reglas de estilo, pero como el explorador web no lo entiende debemos transformar ese SCSS a CSS y enlazarlo así, al final.

2. Para transformar SCSS a CSS debemos decirle a nuestra aplicación cómo hacerlo, y para eso usaremos una gema o biblioteca que nos permitirá darle a nuestra aplicación esa capacidad, esta gema es llamada 'sassc-rails', así que debes ir al archivo Gemfile, y allí buscar la línea `# gem "sassc-rails"` y quitarle el "#" del principio, para al final tener la siguiente línea (aquí estamos descomentando una línea de código):

```ruby
# Use Sass to process CSS
gem "sassc-rails"
```

Ahora esta linea es parte del codigo y podemos ejecutar `bundle install` para instalar esta nueva gema.

`consola`

CONTROL + C (para parar el servidor)

```bash
bundle install
```

Y despues


```bash
bin/dev
```

Para iniciar el servidor otra vez.

3. ahora que Ruby on Rails ya sabe cómo transformar arcvhivos SCSS a CSS, y que ya tenemos nuestros estilos del post, debemos decirle a nuestra aplicación en que punto debemos pemitir que esa hoja de estilo sea colocada. Para este ejercicio, vamos a decidir colocarla en nuestra plantilla principal, para que todas las páginas tengan acceso a nuestra hoja de estilos.

Deste modo debes ir al archivo `app/views/layouts/application.html.erb` y abajo de la línea `<%= stylesheet_link_tag "application", "data-turbo-track": "reload" %>` colocar:

```rhtml
<%= stylesheet_link_tag "post", "data-turbo-track": "reload" %>
```

## 20. Editar y borrar Posts

### Ahora queremos editar nuestros posts

**app/views/posts/show.html.erb**

cambiamos el contenido de todo el archivo por el siguiente:

```rhtml
<%= render @post %>

<div class="text-center edit-links">
  <%= link_to "Editar este post", edit_post_path(@post) %> |
  <%= link_to "Lista de posts", posts_path %>
</div>
```

y añade los siguientes estilos al final de este archivo

**app/assets/stylesheets/post.css.scss**

```css
.edit-links {
  margin-top: 20px;
  margin-bottom: 40px;
}
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

CONTROL + C

```bash
bin/dev
```

### Indica a Devise autorizar este nuevo parámetro  

Actualiza **app/controllers/application_controller.rb**


```ruby
class ApplicationController < ActionController::Base
  protect_from_forgery with: :exception
  before_action :configure_permitted_parameters, if: :devise_controller?
  before_action :i18n_setup

  protected

  def i18n_setup
    I18n.locale = 'es'
  end
  
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

**RETO** añade la clase de estilo "mt-3" al `form-group` del email, pregúntale a tu coach cómo hacerlo y qué significa

### Ahora cambiamos el correo por el nombre

**app/models/post.rb**

Reemplaza

```ruby
user.email
``

con...

```ruby
user.name || user.email
```

## 22. Protege tus posts

### Rodea el enlace de edición con un "si" condicional

De esta manera sólo se pueden ver tus posts. Para poner esto de otra manera: Un usuario sólo puede editar (o borrar) sus posts (y no los posts de otros usuarios ). ¿Tiene algun sentido?


**app/views/posts/show.html.erb**

Reemplaza

```rhtml
<div class="text-center edit-links">
  <%= link_to "Editar este post", edit_post_path(@post) %> |
  <%= link_to "Lista de posts", posts_path %>
</div>
```

con

```rhtml
<% if @post.user == current_user %>
  <div class="text-center edit-links">
    <%= link_to "Editar este post", edit_post_path(@post) %> |
    <%= link_to "Lista de posts", posts_path %>
  </div>
<% else %>
  <div class="text-center edit-links">
    <%= link_to "Lista de posts", posts_path %>
  </div>
<% end %>
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

CONTROL + C

```bash
rails server
```

### Asocia los comentarios

Ahora nuestro modelo **app/model/comment.rb** debe estar configurado para indicar a quién pertenecen los comentarios.

```ruby
class Comment < ApplicationRecord
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


Reemplaza **app/views/posts/_post.html.erb**

```rhtml
<div id="<%= dom_id post %>" class="posts-wrapper row">
  <div class="post">
    <div class="image center-block">
      <%= image_tag post.squared_img, class:'img-fluid' %>
    </div>
    <div class="post-bottom">
      <div class="post-head">
        <div class="avatar">
          <%= image_tag "https://robohash.org/#{post.user.email}.png?set=set4" %>
        </div>
        <div class="user-name">
          <%= post.user_name if post.user %>
        </div>
        <div class="time-ago">
          <%= l post.created_at, format: :short %>
        </div>
      </div>
      <div class="description">
        <%= post.description %>
      </div>
      <hr>
      <div id="comments">
        <% post.comments.each do |comment| %>
          <%= render "comments/comment", comment: comment %>
        <% end %>
      </div>
    </div>
    <%= render "comments/new", post: post %>
  </div>
</div>
```

ahora vamos a añadir dos parciales para lidiar con la creación y visualización de los comentarios, recuerda divide y venceras, dile a tu coach que te explique el concepto de parcial y el rol del helper `render` en la vista de `_post.html.erb`

en la carpeta **app/views/comments** vamos a crear dos archivos con el siguiente contenido

**app/views/comments/_comment.html.erb**

```
<div id="<%= dom_id comment %>" class="comment">
  <div class="user-name">
    <%= comment.user.name %>
  </div>
  <div class="comment-content">
    <%= comment.content %>
  </div>
  <div class="time-ago">
    <%= time_ago_in_words comment.created_at %>
  </div>
</div>
```

**app/views/comments/_new.html.erb**

```
<% if current_user %>
  <div class="comment-like-form row">
    <div class="comment-form col">
      <%= form_for [post, post.comments.new] do |f| %>
        <div class="form-group">
          <%= f.text_field :content, class: 'form-control', placeholder: 'Añade un comentario...' %>
        </div>
      <% end %>
    </div>
  </div>
<% end %>
```

### Los estilos para ponerlo bonito

En **app/javascript/stylesheets/post.css.scss** reemplaza todo el contenido con lo siguiente:

```css
.main-wrapper {
  margin-top: 15px
}

.image {
  text-align: center;
  padding-top: 20px;
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
    color: #125688;
    font-size: 15px;
    line-height: 18px;
    margin-bottom: 15px;
    .avatar {
      display: inline;
      img{
        width: 50px;
        height: 50px;
        border-radius: 50%;
        border: 2px solid #d62d2d;
      }
    }
    .user-name, .time-ago {
      display: inline;
      margin-left: 5px;
    }
    .user-name {
      font-weight: 800;
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
    color: #555;
    margin-bottom: 15px;
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
      font-weight: 800;
      margin-right: 0.3em;
    }
    .time-ago {
      text-align: right;
      color: #777;
      font-size: 10px;
    }
    padding-bottom: 15px;
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
  padding-bottom: 24px;
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

## 25. Turbo Streams - Bonus 1

Tal vez lo has notado, pero cada vez que haces un nuevo cambio, es necesario que refresques la página, este es un comportamiento de la web tradicional, sin embargo, actualmente para no perder la atención del usuario final, es importante mantenerlo con el nuevo contenido aún sin tener que refrescar la página manualmente.

Vamos a realizar está configuración para cada comentario nuevo, cada comentario que se cree se publicará en los exploradores de otros usuarios sin que estos tengan que refrescar su página, y lo vamos a hacer de manera muy sencilla con sólo dos líneas más de código...

## 26. Tener nuestra aplicación en la web

NO LONGER NEEDED

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
