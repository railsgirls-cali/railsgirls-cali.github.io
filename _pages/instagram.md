---
layout: inner
title: Instagram
lead_text: Crea un clon de Instagram desde zero
permalink: /instagram/
---

<div class="repo">
  <h3>Repostitorio de la aplicación</h3>
  <a href="https://github.com/railsgirls-cali/example-instagram">
    https://github.com/railsgirls-cali/example-instagram</a>
</div>

## CONVENCIONES

### 1. consola

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

Con instrucciones y el código/contenido que tienes que agregar o cambiar

```
[...]

código/contenido

[...]
```

## INICIO

## 1. Crea una aplicación nueva

**NOTA**

* Si estás usando C9 y creaste un espacio de trabajo con una plantilla de `Ruby on Rails` ya tienes tu aplicación, puedes seguir hasta el próximo punto `Arranca el servidor de Rails`.
* Si estás usando C9 y creaste un espacio de trabajo con una plantilla de `Rails Tutorial` puedes seguir con las instrucciones abajo.


### Instala la última versión disponible de Ruby on Rails

Rails es un framework de Ruby para desarrollar aplicaciones web, a pesar de estar compuesto de múltiples librerías, Rails es en sí mismo una gema de Ruby.

*"Las gemas en Ruby son las bibliotecas o paquetes (código Ruby empaquetado de una manera predeterminada) de software que se instalan en el sistema para aumentar las funcionalidades del interprete"*.

Para instalar Rails debemos hacer lo siguiente:

`consola`

```
gem install rails
```

Este proceso podría tomar unos minutos...

### Crea una nueva aplicación Rails

Rails viene con un número de generadores que están diseñados para hacer tu ciclo de desarrollo más fácil. Uno de esos, es el generador de nuevas aplicaciones, que crea la estructura base de una aplicación Rails, por lo que no tienes que escribirla por ti misma.

Para usar este generador, abre la consola y ejecuta:

`consola`

```
rails new instagram
```

Esto creará una aplicación Rails llamada **Instagram** en un directorio llamado instagram.

Después de crear la aplicación, entra a su directorio para continuar trabajando directamente en la aplicación:

```
cd instagram
```

Se puede decir que `cd` viene de Change Directory o Cambiar Directorio.

### Arranca el servidor de Rails

`consola`

```
rails server -b 0.0.0.0 -p 8080
```

El comando anterior usa las siguientes opciones:

- **-b** *especifica que el servidor será accesible desde clientes externos, en este caso desde internet utilizando cualquier navegador web si estás usando c9*.
- **-p** *especifica el puerto en el cual el servidor abre la conexión*.


## 2. Página de inicio

En cualquier navegador de tu computador escribe la URL: [localhost:3000](localhost:3000). Esta es la página de inicio por defecto para las aplicaciones Rails.

**NOTA** Si estás usando C9 no vas a poder acceder a la página de inicio en tu explorador usando la URL anterior, necesitas una URL especial, para el caso del taller la URL será generada de la siguiente forma:

http://**nombre_del_proyecto**-**tu_usuario_de_c9**.c9users.io/

Deberías ver la página de información por defecto de Rails.

La página "Welcome Aboard" es la primera prueba para una nueva aplicación Rails: Ésta asegura que tienes el software configurado correctamente para servir una página.


## 3. Crea una nueva página

Para crear nuestra nueva página, necesitas crear como mínimo un controlador y una vista.

El propósito de un controlador es recibir las peticiones (requests) de la aplicación. El enrutamiento (routing) decide qué controlador recibe qué petición.

A menudo, hay más de una ruta para cada controlador, y diferentes rutas pueden ser servidas por diferentes acciones (actions). El propósito de cada acción es obtener información para pasarla después a la vista.

El propósito de una vista es mostrar la información en un formato legible para los humanos. Una distinción importante que hacer, es que es el controlador, y no la vista, donde la información es recolectada. La vista sólo debería mostrar la información. Por defecto, las plantillas de las vistas están escritas en un lenguaje llamado ERB (del inglés, Embedded Ruby), que se procesa automáticamente para cada petición servida por Rails.

Para crear un nuevo controlador, necesitas ejecutar el generador de controladores y decirle que quieres un controlador llamado por ejemplo `pages` con una acción llamada `home`. Para ello, ejecuta lo siguiente:

**NOTA** El primer tab de tu consola ya tiene el servidor de Rails corriendo que lanzaste con el comando:

```
rails server -b 0.0.0.0 -p 8080
```

Ahora tienes que abrir un nuevo tab.
En el terminal aparecerá un nuevo prompt `$ ` donde puedes ejecutar:


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
invoke    coffee
create      app/assets/javascripts/pages.coffee
invoke    scss
create      app/assets/stylesheets/pages.scss
```

Los archivos más importantes de éstos son por supuesto el controlador, que se encuentra en **app/controllers/pages_controller.rb** y la vista, que se encuentra en **app/views/pages/home.html.erb**.


### Actualiza el texto en la nueva página

Abre el archivo **app/views/pages/home.html.erb** en tu editor de texto y edítalo para que contenga sólo está línea de código:

```html
<h1>¡Bienvenidos a Instagram!</h1>
```

En tu navegador, ve a la URL : [http://**nombre_del_proyecto**-**tu_usuario_de_c9**.c9users.io/pages/home](http://**nombre_del_proyecto**-**tu_usuario_de_c9**.c9users.io/pages/home) y ve la nueva página que se acaba de crear.


### Mostrar la página de inicio de tu aplicación (Home)

¿Cómo conectar la raíz de tu sitio a un controlador y acción específica?

Debemos configurar la ruta de acceso a la aplicación editando el archivo `config/routes.rb`, para esto debemos cambiar la siguiente línea en el mismo:

**config/routes.rb**

Reemplazar la línea

```ruby
get 'pages/home'
```

...por:

```ruby
root 'pages#home'
```

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


## 5. ¡Instalemos Bootstrap!

### Añade la gema de Bootstrap Y Sass

*"Las gemas en Ruby son las bibliotecas o paquetes (código Ruby empaquetado de una manera predeterminada) de software que se instalan en el sistema para aumentar las funcionalidades del interprete"*.

- **Bootstrap** es una biblioteca multiplataforma o conjunto de herramientas de código abierto para diseño de sitios y aplicaciones web. Contiene plantillas de diseño con tipografía, formularios, botones, cuadros, menús de navegación y otros elementos de diseño basado en HTML y CSS, así como extensiones de JavaScript adicionales.

- **Sass** (acrónimo de Syntactically Awesome StyleSheets) es una extensión de CSS que añade características muy potentes y elegantes a este lenguaje de estilos. Sass permite el uso de variables, reglas CSS anidadas, mixins, importación de hojas de estilos y muchas otras características, al tiempo que mantiene la compatibilidad con CSS.

En

**/Gemfile**

Y justo antes de `group :development, :test do` inserta:

```ruby
[...]

gem 'bootstrap-sass'

[...]
```

### Siempre pare el servidor con `CONTROL + C` y corre `bundle install` para instalar una nueva gema

`consola`

```bash
CONTROL + C
bundle install
```

### Vuelve a iniciar el servidor

`consola`

```bash
rails server -b 0.0.0.0 -p 8080
```

### Crea un nuevo documento SCSS

Una vez instalado Bootstrap en nuestra aplicación, crearemos un nuevo documento SASS en `app/assets/stylesheets/custom_bootstrap.scss` para importar todas las funcionalidades CSS de boostrap a nuestro proyecto. En este nuevo documento debemos añadir lo siguiente:

**app/assets/stylesheets/custom_bootstrap.scss**

```
@import "bootstrap";
```

### Importa el Javascript para Bootstrap

Igualmente, en el archivo `app/assets/javascripts/application.js` debemos agregar el código de abajo para importar todas las funcionalidades JS de Boostrap en nuestro proyecto.

**app/assets/javascripts/application.js**

```
[...]
//= require bootstrap-sprockets
[...]
//= require_tree .
```

### Añade el viewport
##### Esto sirve para permitir que tu app se vea bien en varios tamaños de pantalla
**views/layouts/application.html.erb**

Después del `<head>` y antes del `<title>`.

Inserta:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### Vuelve a iniciar el servidor

`consola`

```bash
CONTROL + C
rails server -b 0.0.0.0 -p 8080
```

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
<nav class="navbar navbar-default" role="navigation">
  <div class="container">
    <!-- Brand and toggle get grouped for better mobile display -->
    <div class="navbar-header">
      <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-ex1-collapse">
        <span class="sr-only">Toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <%= link_to "Instagram", root_path, class: "navbar-brand" %>
    </div>

    <!-- Collect the nav links, forms, and other content for toggling -->
    <div class="collapse navbar-collapse navbar-ex1-collapse">
      <ul class="nav navbar-nav navbar-right">
        <li><%= link_to "Home", root_path %></li>
        <li><%= link_to "Quiénes somos", about_path %></li>
      </ul>
    </div><!-- /.navbar-collapse -->
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

**app/assets/stylesheets/custom_bootstrap.scss**

Reemplaza:

```scss
@import 'bootstrap';
```

por los siguientes estilos:

```scss
@import url(http://fonts.googleapis.com/css?family=Lato:400,700);
@import url(http://fonts.googleapis.com/css?family=Oleo+Script);

$body-bg:                          #fafafa !important;
$font-family-sans-serif:           'Lato', 'Helvetica Neue', Helvetica, Arial, sans-serif;
$navbar-height:                    70px;
$navbar-default-bg:                white;
$navbar-default-brand-color:       #3897F0;
$navbar-default-link-color:        #3897F0;
$brand-primary:                    #3897F0 !default;
$jumbotron-bg:                     white;

@import 'bootstrap-sprockets';
@import 'bootstrap';

.navbar-default .navbar-brand {
  font-family: 'Oleo Script', cursive;
  font-size: 25px;
  font-weight: bold;
  color: #262626;
}

.navbar-nav {
  font-weight: bold;
}
```


## 9. Añadir Devise para Autenticación de usuarios

### Añade la gema de Devise

La mayoría de las aplicaciones web necesitan que los usuarios puedan crear una cuenta, modificar su perfil, iniciar y cerrar sesión. En el contexto de rails hay una gema que se integra naturalmente con él y gestiona estos componentes; esta gema se llama Devise.

**/Gemfile**

```ruby
[...]
gem 'devise'
[...]
```

### Siempre pare el servidor con `CONTROL + C` y corre `bundle install` para instalar una nueva gema

`consola`

```bash
CONTROL + C
bundle install
```

### Vuelve a iniciar el servidor

`consola`

```bash
rails server -b 0.0.0.0 -p 8080
```


## 10. Configuración de Devise

**NOTA** El primer tab de tu consola todavía tiene el servidor de Rails corriendo.
Sigue usando el otro tab.

### Instala Devise

`consola`

```bash
rails generate devise:install
```

### Crea las vistas de Devise

Generar las vistas para la personalización del manejo de sesiones de usuario.

`consola`

```
rails g devise:views
```

### Crea un modelo de usuario

`consola`

```bash
rails generate devise User
```

La línea de arriba crea un modelo de usuario y un nuevo archivo: **app/models/user.rb**

Ve a **db/migration** y deberías tener en los archivos algo así como **db/migration/20170218022322_devise_create_users.rb**

El número es la fecha de creación.

### Migra la base de datos

`consola`

```bash
rake db:migrate
```

Este comando toma el archivo de migración y lo ejecuta, de manera que genere tablas en la base de datos.


### Vuelve a iniciar el servidor

```bash
CONTROL + C (para parar el servidor)
rails server -b 0.0.0.0 -p 8080 (para volver a iniciar el servidor)
```

Tendrás que reiniciar la aplicación cada vez que instales una gema o cada vez que ejecutes `rake db:migrate`


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
<ul class="nav navbar-nav navbar-right">
  <li><%= link_to "Home", root_path %></li>
  <li><%= link_to "Quiénes somos", about_path %></li>
</ul>
```
por

```rhtml
<ul class="nav navbar-nav navbar-right">
  <li><%= link_to "Home", root_path %></li>
  <li><%= link_to "About", about_path %></li>
  <% if user_signed_in? %>
    <li><%= link_to "Cerrar sesión", destroy_user_session_path, method: :delete %></li>
  <% else %>
    <li><%= link_to "Regístrate", new_user_registration_path %></li>
    <li><%= link_to "Iniciar sesión", new_user_session_path %></li>
  <% end %>
</ul>
```

**NOTA** Usa el tabulador, la tecla Tab (Tab ↹) nos permite indentar el texto que este en nuestra selección y así mantener el código organizado y indentado.


## 13. Cambia las vistas de Devise

### Reemplaza el código para cada una de las vistas de Devise

**app/views/devise/registrations/new.html.erb**

#### *Esta vista se encarga del formulario de registro de usuarios en tu app.*

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

  <%= render "devise/shared/links" %>
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

  <%= render "devise/shared/links" %>

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

  <%= render "devise/shared/links" %>
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

  <%= render "devise/shared/links" %>
</div>
```
### Añade estos estilos para que tus formularios se vean más geniales <3

Al final del archivo: **app/assets/stylesheets/custom_bootstrap.scss**

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
<li><%= link_to "Mi cuenta", edit_user_registration_path %></li>

```

## 14. Genera el scaffold para Posts

`Posts` serán nuestras publicaciones o, mejor dicho, ¡Las imágenes que publicamos en nuestro Instagram!

### Genera un scaffold para Posts

Un scaffold es un generador automático de modelo + controlador + vistas

```bash
rails generate scaffold posts description:string
rake db:migrate
```

El scaffold también crea un archivo de estilos CSS basicos pero nosotros vamos a usar nuestro propio CSS así que podemos borrar este archivo.

**/app/assets/stylesheets/scaffolds.scss**


## 15. Simplifiquemos el controlador de Posts

**app/controllers/posts_controller.rb**

##### Reemplaza todo el contenido del controlador

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

Modifica el parcial del formulario **apps/views/posts/_form.html.erb**

Reemplaza todo el contenido por:

```rhtml
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

Cambia todo lo que hay en estos dos archivos: **app/views/posts/edit.html.erb**, **app/views/posts/new.html.erb** por:

```rhtml
<div class="form-wrapper">

  <%= render 'form' %>

</div>
```

### Añade un enlace en el navbar (barra de navegación) para crear un nuevo post

**app/views/layouts/_header.html.erb**

Debajo de `<% if user_signed_in? %>`:

```rhtml
<li><%= link_to 'Nuevo post', new_post_path %></li>
```

### Redireccionamos la raíz de nuestra aplicación al `index` de Posts

##### (no te diremos en qué archivo, es un desafío ;) , si tienes dudas, ¡Pregúntale a uno de tus mentores! )

reemplaza `root 'pages#home'` por `root 'posts#index'`

## 17. Posts, Usuarios y Asociaciones

#### Recursos

**Asociaciones:** https://makeitrealcamp.gitbook.io/ruby-on-rails-5/asociaciones

### Configura tus asociaciones

Un Post `belongs_to` un Usuario.

##### Una Publicación ***pertenece*** a un Usuario

**app/models/post.rb**

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
rake db:migrate
```
* ##### Recuerda que hacemos `rake db:migrate` porque acabamos de crear una migración.

* ##### Cada vez que hagas una migración, debes reiniciar el servidor de Rails.

`consola`

```bash
CONTROL + C (para parar el servidor)
rails server -b 0.0.0.0 -p 8080 (para volver a iniciar el servidor)
```


### Un Usuario `has_many` Posts

##### Un Usuario ***tiene*** muchas Publicaciones

**app/models/user.rb**

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

Recursos: https://github.com/plataformatec/devise

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

## 19. Sube imágenes con Paperclip

### Instala el procesador de imágenes ImageMagick

Paperclip requiere la instalación de ImageMagick. Necesitas esto para procesamiento de imagen. Para instalar ImageMagick, usa los comandos abajo.

`consola`

```bash
sudo apt-get update
sudo apt-get install imagemagick
```

### Instala la gema Paperclip

Paperclip es una gema que permite mediante el comando `has_attached_file` poder adjuntar imágenes de manera fácil.

https://github.com/thoughtbot/paperclip

**/Gemfile**

```ruby
gem 'paperclip'
```

`consola`

```
bundle install
```
Actualiza el model `Post`

**/app/models/post.rb**

```ruby
class Post < ActiveRecord::Base
  belongs_to :user
  has_attached_file :image, styles: { medium: "600x600#" }
  validates_attachment_content_type :image, :content_type => /\Aimage\/.*\Z/
end
```

### Genera la migración de paperclip

`consola`

```
rails generate paperclip post image
```

Ejecuta y verifica la migración

`consola`

```bash
rake db:migrate
```

### Vuelve a iniciar el servidor después de agregar una librería (gema)

`consola`

```bash
CONTROL + C
rails server -b 0.0.0.0 -p 8080
```

### Edita el formulario de Post

**/app/views/posts/_form.html.erb**

Reemplaza la primera línea por:

```rhtml
<%= form_for @post, html: { multipart: true } do |f| %>
```

Y justo antes de

```rhtml
<div class="form-group">
    <%= f.label :description %>
```

Añade:

```rhtml
  <div class="form-group">
    <%= f.label :image %>
    <%= f.file_field :image %>
  </div>
```

### Actualiza el controlador de Posts para parámetros "strong"

**/app/controllers/concerns/posts_controller.rb**

`def post_params`

```ruby

.
  def post_params
    params.require(:post).permit(:description, :image)
  end
.

```

### Actualiza la vista `index` de Posts

**/app/views/posts/index.html.erb**

```rhtml
<% if user_signed_in? %>
  <div class="main-wrapper">
    <div class="row">
      <% @posts.each do |post| %>
        <div class="col-sm-4">
          <div class="image center-block">
            <%= link_to (image_tag post.image.url(:medium), class:'img-responsive'), post_path(post) %>
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
      <%= image_tag @post.image.url(:medium),class:'img-responsive' %>
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

Abajo del archivo **app/assets/stylesheets/custom_bootstrap.scss**

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

**app/assets/stylesheets/custom_bootstrap.scss**

```css
.edit-links {
  margin-top: 20px;
  margin-bottom: 40px;
}
```

y en **app/views/posts/edit.html.erb**, lo más arriba, añade

```rhtml
<div class="text-center">
  <%= image_tag @post.image.url(:medium) %>
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
rake db:migrate
```

### Vuelve a iniciar el servidor después de correr una migración

`consola`

```bash
CONTROL + C
rails server -b 0.0.0.0 -p 8080
```

### Indica a Devise autorizar este nuevo parámetro  

Actualiza **app/controllers/application_controller.rb**


```ruby
class ApplicationController < ActionController::Base
 protect_from_forgery with: :exception
 before_filter :configure_permitted_parameters, if: :devise_controller?

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

**app/views/posts/index.html.erb**

Reemplaza

```rhtml
<%= post.user.email if post.user %>
```

con...

```rhtml
<%= post.user.name if post.user %>
```

y **app/views/posts/show.html.erb**

con...

```rhtml
<%= @post.user.name if @post.user %>
```

## 22. Protege tus posts

### Rodea el enlace de edición con un "si" condicional

De esta manera sólo se pueden ver tus posts. Para poner esto de otra manera: Un usuario sólo puede ver sus posts (y no los posts de otros usuarios). ¿Tiene algún sentido?


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

### Proteger los posts también desde el controlador

**app/controllers/posts_controller.rb**

Agrega debajo de `private`

```ruby
private

def owned_post  
  unless current_user == @post.user
    flash[:alert] = "¡Este post no te pertenece!"
    redirect_to root_path
  end
end
```

Después, inserta un `before_action` en la parte superior del controlador, especificando el método `owned_post` solamente para las acciones de edición, actualización y destruir.

```ruby
before_action :owned_post, only: [:edit, :update, :destroy]
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
rake db:migrate
```

### Vuelve a iniciar el servidor después de correr una migración

`consola`

```bash
CONTROL + C
rails server -b 0.0.0.0 -p 8080
```

### Asocia los comentarios

Ahora nuestro modelo **app/model/comment.rb** está configurado para indicar a quién pertenecen los comentarios.

```ruby
class Comment < ActiveRecord::Base  
  belongs_to :user
  belongs_to :post
end
```

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

**app/controllers/comments_controller.rb**

```ruby
class CommentsController < ApplicationController
  before_action :set_post

  def create  
    @comment = @post.comments.build(comment_params)
    @comment.user_id = current_user.id

    if @comment.save
      flash[:success] = "¡Has comentado este post!"
      redirect_to :back
    else
      flash[:alert] = "Revisa el formulario de comentarios, algo salió mal :/"
      render root_path
    end
  end

  def destroy  
    @comment = @post.comments.find(params[:id])

    @comment.destroy
    flash[:success] = "Comentario eliminado :("
    redirect_to root_path
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
      <%= image_tag @post.image.url(:medium), class:'img-responsive' %>
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
          <%= f.text_field :content, placeholder: 'Añade un comentario...' %>
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

En **app/assets/stylesheets/custom_bootstrap.scss**

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

## Tener nuestra aplicación en la web

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
heroku run rake db:migrate #Para correr las migraciones
```

## Bonus: Comentarios con AJAX

¿Cómo intercambiar información con el servidor sin tener que refrescar la página? Ese es el problema que soluciona [Ajax](https://es.wikipedia.org/wiki/AJAX).
En nuestro caso sería como añadir comentarios sin tener que refrescar la página.

- recursos: [JavaScript, jQuery y Ajax](http://blog.makeitreal.camp/javascript-jquery-y-ajax)

### Mueve los comentarios en un parcial

Ajax en Rails se maneja con parciales, entonces...

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

### Ahora podemos cambiar `_post.html.erb`

Acabamos de mudar el comentario aparte de nuestro, formulario en un archivo separado. Ahora, vamos a tener que ajustar nuestro post parcial para seguir monstrando los comentarios de manera apropiada.

En **app/views/posts/_post.html.erb**

Reemplaza

```rhtml
<% post.comments.each do |comment| %>
  <div class="comment">
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
<% end %>
```

con...


```rhtml
<%= render post.comments, post: post %>
```

Y sigue funcionando igual.


### Añadiendo `remote: true` a nuestro formulario

En **app/views/posts/_post.html.erb**

reemplaza

```rhtml
<% if post.comments %>
  <%= render post.comments, post: post %>
<% end %>
```

con...

```rhtml
<div class="comments" id="comments_<%= post.id %>">
  <% if post.comments %>
    <%= render post.comments, post: post %>
  <% end %>
</div>
```

y las líneas

```rhtml
<%= form_for [post, post.comments.new] do |f| %>
  <%= f.text_field :content, placeholder: 'Añade un comentario...' %>
<% end %>
```

con...

```rhtml
<%= form_for([post, post.comments.build], remote: true) do |f| %>
  <%= f.text_field :content, placeholder: 'Añade un comentario...', id: "comment_content_#{post.id}" %>
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

Al final de esta línea y antes de `do`, añade `remote: true`

```rhtml
<%= link_to post_comment_path(post, comment), method: :delete, data: { confirm: "¿Estás segura?" } do %>
```

### Añade la respuesta Javascript para la acción del controlador

Al igual que antes, ahora podemos asegurar que rails responde no sólo con HTML, sino también con Javascript.

Añade el método `responds_to` a la acción `destroy` dentro del `comments_controller`

```ruby
def destroy
  @comment = @pin.comments.find(params[:id])

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
