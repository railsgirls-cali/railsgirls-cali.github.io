---
layout: inner
title: Instagram
lead_text: Crea un clon de Instagram desde zero
permalink: /instagram/
---




## 1. Crea una aplicación nueva

### Crea una nueva aplicación Rails

consola

```
rails new instagram

cd instagram
```

### Arranca el servidor de Rails

consola

```
rails server
```


## 2. Página de inicio

En el navegador, ve a la URL: [localhost:3000](localhost:3000) . Esta es la página de inicio por defecto para las aplicaciones Rails.

### Crea una nueva página

consola

```
rails generate controller pages home
```

En tu navegador, ve a la URL : [localhost:3000/pages/home](localhost:3000/pages/home) y ve la nueva página en blanco que se acaba de crear.


### Actualiza el texto en la nueva página

**app/views/pages/home.html.erb**

```html
<h1>¡Bienvenidos a mi aplicación!</h1>
```

## 3. Crea la raíz de la aplicación

### Mostrar la página de inicio de tu aplicación

**config/routes.rb**

Reemplazar la línea

```ruby
get "pages/home"
```

...por:

```ruby
root "pages#home"
```

## 4. Crea más paginas

### Añade una nueva acción en el controlador

**app/controllers/pages_controller.rb**

```ruby
def about
end
```

###  Crea el código HTML en la vista

**app/views/pages/about.html.erb**

```html
<h1>¿Quiénes somos?</h1>
<p>Estamos trabajando en nuestra aplicación Instagram</p>
```

###  Agregamos la ruta

**config/routes.rb**

```ruby
get "about" => "pages#about"
```

## 5. ¿Embedded Ruby?

### Cambia el enlace HTML a un enlace embebido de ruby
**app/views/pages/home.html.erb**

```rhtml
<%= link_to "here", "#" %>
```

En HTML, un enlace es así

```html
<a href="#"> aquí </a>
```

Estas son etiquetas de Ruby

```erb
< % = % >
```

En Ruby on Rails un enlace se verá así

```erb
<%= link_to "aquí", "#" %>
```

## 6. ¡Instalemos Bootstrap!

### Añade la gema de Bootstrap

**/Gemfile**

```ruby
gem 'bootstrap-sass'
```

### Siempre corre `bundle install` para instalar una nueva gema

consola

```
bundle install
```

### Entendamos el documento application.css

**app/assets/stylesheets/application.css**


### Crea un nuevo documento SCSS

**app/assets/stylesheets/custom_bootstrap.css.scss**

```scss
@import 'bootstrap';
```

### Vuelve a iniciar el servidor

consola

```bash
CONTROL + C
rails server
```

## 7. Añade elementos de Bootstrap a la página

### ¡Añade un contenedor a tu aplicación!

**views/layouts/application.html.erb**

Dentro de la etiqueta `<body>`, reemplaza

```rhtml
<%= yield %>
```

por...

```rhtml
<%= link_to "Home", root_path %>
<%= link_to "About", about_path %>
<div class="container">
    <%= yield %>
</div>
```

### Crea un parcial de encabezado

Crea el archivo **app/views/layouts/_header.html.erb**

### Crea un enlace al parcial

**app/views/layouts/application.html.erb**

Después del `<body>`

```erb
<%= render 'layouts/header' %>
```

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
        <li><%= link_to "About", about_path %></li>
      </ul>
    </div><!-- /.navbar-collapse -->
  </div>
</nav>
```

### Importa el Javascript para Bootstrap
**app/assets/javascripts/application.js**

```js

//= require jquery
//= require jquery_ujs
//= require bootstrap-sprockets
//= require turbolinks
//= require_tree .
```

### Añade el viewport
**views/layouts/application.html.erb**

Después del `<head>` y antes del `<title>`.

Inserta:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### Añade el encabezado a la página de inicio

**views/pages/home.html.erb**

```rhtml
<div class="jumbotron">
	<h1>¡Bienvenidos a mi aplicación!</h1>
	Haz clic aquí para <%= link_to "Registrarte", "#", class: "btn btn-primary" %>
</div>
```

## 8. Personalicemos Bootstrap

### Por ejemplo, actualicemos la barra de navegación

**app/views/layouts/_header.html.erb**

```html
<nav class="navbar navbar-default" role="navigation">
```

## 9. Mejoremos el diseño

### Cambios de estilo

**app/assets/stylesheets/custom_bootstrap.css.scss**

```scss
@import url(http://fonts.googleapis.com/css?family=Lato:400,700);

$body-bg:                          #fafafa !important;
$font-family-sans-serif:           'Lato', 'Helvetica Neue', Helvetica, Arial, sans-serif;
$navbar-height:                    54px;
$navbar-default-bg:                white;
$navbar-default-brand-color:       #125688;
$navbar-default-link-color:        #125688;
$brand-primary:                    #4090DB;
$jumbotron-bg:                     white;

@import 'bootstrap-sprockets';
@import 'bootstrap';


.navbar-brand {
  font-weight: bold;
}
```


### Añadimos una clase "text-center" y un botón "Iniciar sesión"

**/app/views/pages/home.html.erb**

```rhtml
<div class="jumbotron text-center">
  <h1>¡Bienvenidos a mi aplicación!</h1>
  <p>
   <%= link_to "Iniciar sesion", "#", class: "btn btn-default btn-lg" %>
   <%= link_to "Regístrate", "#", class: "btn btn-primary btn-lg" %>
  </p>    
</div>
```

## 10. Añadir Devise

### Añade la gema de Devise

**/Gemfile**

```ruby
gem 'devise'
```

consola

```
bundle install
```

### Instala Devise

```bash
rails generate devise:install
```

## 11. Configuración de Devise

### URLs por defecto

**config/environments/development.rb**

```ruby
config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
```

**config/environments/production.rb**

```ruby
config.action_mailer.default_url_options = { host: 'http://instagram.herokuapp.com/' }
```


### Mensajes flash

Los mensajes flash son los mensajes en sitios web que dicen " Gracias por registrarse en " o "Gracias por suscribirse a"

**app/views/layouts/application.html.erb**

```rhtml
<div class="container">

  <% flash.each do |name, msg| %>
     <%= content_tag(:div, msg, class: "alert alert-#{name}") %>
  <% end %>

  <%= yield %>

</div>
```

### Desactiva la precompilación

**config/application.rb**

```ruby
config.assets.initialize_on_precompile = false
```

### Crea las vistas de Devise

consola

```
rails g devise:views
```

## 12. Crea usuarios con Devise

### Crea un modelo de usuario

```bash
rails generate devise user
```

Esta línea de arriba crea un modelo de usuario y un nuevo archivo: **app/models/user.rb**

Ve a **db/migration** y deberías tener en los archivos algo así como **db/migration/20130922022322_devise_create_users.rb**

El número es la fecha de creacíon

### Migra la base de datos

consola

```bash
rake db:migrate
```

Este comando toma el archivo de migración y lo ejecuta, de manera que genere tablas en la base de datos

### Vuelve a iniciar el servidor

```bash
CONTROL + C (para parar el servidor)
rails server (para volver a iniciar el servidor)
```

Tendrás que reiniciar la aplicación cada vez que instales una gema o cada vez que ejecutes `rake db:migrate`

## 13. Registrar nuevos usuarios o iniciar sesíon

```
rake routes
```

Muestra todas las rutas disponibles para tu aplicación. Podrás añadir más a lo largo del camino

### Modifica la vista de inicio

**app/views/pages/home.html.erb**

```rhtml
<div class="jumbotron text-center">
 <h1>¡Bienvenidos a mi aplicación!</h1>
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

### Modifica el parcial de navegacíon

**app/views/layout/_header.html.erb**

```rhtml
<nav class="navbar navbar-default" role="navigation">
    <ul class="nav navbar-nav navbar-right">
    <li><%= link_to "Home", root_path %></li>
    <li><%= link_to "About", about_path %></li>
    <% if user_signed_in? %>
      <li><%= link_to "Cerrar sesión", destroy_user_session_path, method: :delete %></li>
    <% else %>
      <li><%= link_to "Iniciar sesión", new_user_session_path %></li>
    <% end %>
  </ul>
</nav>
```

## 14. Cambia las vistas de Devise

### Modifica el código para cada una de las vistas de Devise

**app/views/devise/registrations/new.html.erb**

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
### Añade unos estilos

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

## 15. Genera el scaffold para Posts

### Genera un scaffold para Posts

```bash
rails generate scaffold posts description:string
rake db:migrate #corre la migración
```


## 16. Simplificando el controlador de Posts

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

## 17. Las vistas de posts

### Esto se llama el parcial "formulario"

**apps/views/posts/new.html.erb**

```rhtml
<%= render 'form' %>
```

**apps/views/posts/_form.html.erb**

```rhtml
<%= form_for(@post) do |f| %>
  <% if @post.errors.any? %>
    <div id="error_explanation">
      <h2><%= pluralize(@post.errors.count, "error") %> no permiten que este post sea guardado:</h2>

      <ul>
      <% @post.errors.full_messages.each do |msg| %>
        <li><%= msg %></li>
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

### Para mantener nuestros estilos, añade las siguientes vistas dentro de un form-wrapper

**app/views/posts/edit.html.erb**, **app/views/posts/new.html.erb**

### Además, elimina el archivo

**app/views/assets/stylesheets/scaffolds.scss**

### Añade un enlace para crear un nuevo post al navbar

**app/views/layouts/_header.html.erb**

Debajo de `<% if user_signed_in? %>`:

```rhtml
<li><%= link_to 'Nuevo post', new_post_path %></li>
```

### Redireccionamos la raíz de nuestra aplicación al `index` de Posts

reemplaza `root "pages#home"` por `root "posts#index"`

## 18. Posts, Usuarios y Asociacíon

Recursos

asociacíon: http://guides.rubyonrails.org/association_basics.html

### Configura tus asociaciones

Un Post `belongs_to` un Usuario

**app/models/post.rb**

```ruby
class Post < ActiveRecord::Base
	belongs_to :user
end
```


### Genera una nueva migración de índice de un usuario

```bash
rails generate migration add_user_id_to_posts user_id:integer:index
rake db:migrate
```


### Inicia la consola de Rails

La consola de Rails nos permite interactuar directamente con los datos en la base de datos. Usa la consola para actualizar directamente los datos , o  solo para probar el código Ruby antes de integrarlo a tu proyecto

```
rails console
```

Una vez en la consola ...

```bash
> Post.connection #Esto establece una conexión con la base de datos ( y escupe una gran cantidad de datos innecesarios)
> Post.inspect #muestra todos los parámetros para un Post
> post = Post.first #Nos trae el primer Post asegurate que la primer letra es MAYÚSCULA
> post.user #Nos muestra el usuario del post.
```

Detén la consola cuando termines

CONTROL + D #cierra la consola

### Un Usuario `has_many` Posts  

**app/models/user.rb**

```ruby
class User < ActiveRecord::Base

  devise :database_authenticatable, :registerable,
         :recoverable, :rememberable, :trackable, :validatable

  has_many :posts
end
```


### Verificamos que funcione...

De vuelta en la consola de Rails (en nuestra consola) vamos a configurar un ID de usuario en un Post.

```bash
> post = Post.first
> post #echar una mirada al post
> post.user_id = 1
> post.save

> user = User.first
> user.posts
```

## 19. Autorización : ¿Quién puede? ¿Quién no puede?

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
      params.require(:post).permit(:description, :image)
    end
end
```

### Agreguemos autenticación de usuarios con Devise

Recursos: https://github.com/plataformatec/devise

Añade `before_action` al Controlador Posts

**app/controllers/posts_controller.rb**

```ruby
before_action :authenticate_user!, except: [:index, :show]
```


### Añade el método `correct_user`

Añade el método `before_action` a tu controlador de Posts

**app/controllers/posts_controller.rb**

```ruby
before_action :correct_user, only: [:edit, :update, :destroy]
```

## 20. Sube imágenes con Paperclip

### Instala el procesador de imagenes ImageMagick

En la consola

```bash
sudo apt-get install imagemagick
```

### Instala la gema Paperclip

https://github.com/thoughtbot/paperclip

**/Gemfile**

```ruby
gem 'paperclip', '~> 4.2'
```

Ejecuta en tu consola:

```
bundle install
```

**/app/models/post.rb**

```ruby
class Post < ActiveRecord::Base
  belongs_to :user
  has_attached_file :image, :styles => { :medium => "640x", :thumb => "100x100>" }
  validates_attachment_content_type :image, :content_type => /\Aimage\/.*\Z/
end
```

### Genera la migración de paperclip

```
rails generate paperclip post image
```

Ejecuta y verifica la migración

```bash
rake db:migrate
rake db:migrate:status
```

### Vuelve a iniciar el servidor después de agregar una librería (gema)

```bash
CONTROL + C
rails server
```

### Edita el formulario de Post
**/app/views/posts/_form.html.erb**

```rhtml
<%= form_for @post, html: { multipart: true } do |f| %>
.
.
.
  <div class="form-group">
    <%= f.label :image %>
    <%= f.file_field :image, class: "form-control" %>
  </div>
.
.
.
```

### Actualiza el controlador de Posts para parámetros "strong"

**/app/controllers/concerns/posts_controller.rb**

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
<div class="posts-wrapper row">
  <% @posts.each do |post| %>
    <div class="post">
      <div class="post-head">
        <div class="name">
          <%= post.user.email if post.user %>
        </div>
      </div>
      <div class="image center-block">
        <%= link_to (image_tag post.image.url(:medium), class:'img-responsive'), post_path(post) %>
      </div>
      <p class="description">
        <%= post.description %>
      </p>
    </div>
  <% end %>
</div>
```
### Con el estilo Instagram

```css
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
  border-bottom: 1px solid #eeefef;
  border-top: 1px solid #eeefef;
}

.description {
  padding: 24px 24px;
  font-size: 15px;
  line-height: 18px;
}
```

### Elimina los Posts creados por usuarios No Registrados

```bash
rails console
Post.first
post = Post.first
post.destroy
Post.first.destroy
```

### Actualiza la vista `show` de Posts

**/app/views/posts/show.html.erb**

```rhtml
<div class="posts-wrapper row">
  <div class="post">
    <div class="post-head">
      <div class="name">
        <%= @post.user.email if @post.user %>
      </div>
    </div>
    <div class="image center-block">
      <%= image_tag @post.image.url(:medium) %>
    </div>
    <p class="description">
      <%= @post.description %>
    </p>
  </div>
</div>

```

## Editar y borrar Posts

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

y añade los siguiente estilos

**app/assets/stylesheets/custom_bootstrap.css.scss**

```css
.edit-links {
  margin-top: 20px;
  margin-bottom: 40px;
}
```

y en **app/views/posts/show.html.erb**, lo más arriba, añade

```rhtml
<div class="text-center">
  <%= image_tag @post.image.url(:medium) %>
</div>
```

### ¿Y si queremos borrar nuestro post?

**app/views/posts/show.html.erb**

Completamente abajo colocamos:

```rhtml
<div class="text-center edit-links">
  <%= link_to "Borrar Post", post_path(@post), method: :delete, data: { confirm: "¿Estás segura que quieres eliminar este post?" } %>
  |
  <%= link_to "cancelar", posts_path %>
</div>
```

## Añade un nombre de usuario para personalizar la aplicación

### Crea la migración en la base de datos

consola

```bash
rails generate migration AddNameToUsers name:string
```

### Migra la base de datos

consola

```bash
rake db:migrate
```

### Añade al fomulario de registro el campo nombre  

**app/views/devise/registrations/edit.html.erb**

```rhtml
.
     <div class="form-group">
       <%= f.label :name %>
       <%= f.text_field :name, class: "form-control", autofocus: true %>
     </div>
.
```

### Indica a Devise autorizar este nuevo parámetro  

**app/controllers/application_controller.rb**


```ruby
class ApplicationController < ActionController::Base
 # Prevent CSRF attacks by raising an exception.
 # For APIs, you may want to use :null_session instead.
 protect_from_forgery with: :exception
 before_filter :configure_permitted_parameters, if: :devise_controller?

protected

 def configure_permitted_parameters
   devise_parameter_sanitizer.for(:sign_up) << :name
   devise_parameter_sanitizer.for(:account_update) << :name
 end
end
```

### Y también agregamos el campo en las vistas

**app/views/devise/registrations/new.html.erb**, **app/views/devise/registrations/edit.html.erb**

```rhtml
.
  <div class="form-group">
    <%= f.label :name %>
    <%= f.text_field :name, autofocus: true, class: "form-control" %>
  </div>
.
```

### Terminamos con un nuevo controlador

Creaa el archivo **app/controllers/registrations_controller.rb**:

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

Reemplaza

```ruby
devise_for :users
```

con...

```ruby
devise_for :users, :controllers => { registrations: 'registrations' }
```

### Ahora cambiamos el correo por el nombre

**app/views/posts/index.html.erb**, **app/views/posts/index.html.erb**

Reemplaza

```rhtml
<%= post.user.email if post.user %>
```

con...

```rhtml
<%= post.user.name if post.user %>
```

## Protege tus posts

### Rodea el enlace de edición con un "si" condicional

De esta manera sólo se pueden ver tus posts. Para poner esto de otra manera: Un usuario sólo puede ver sus posts (y no los posts de otros usuarios ). ¿Tiene algun sentido?


**app/views/posts/show.html.erb**

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

## Añadiremos la opción de comentar nuestros posts

### Empezamos por generar un modelo

```bash
rails g model Comment user:references post:references content:text
```

Este comando nos genera una migración **db/migrate/** para añadir los campos en la base de datos y un modelo **app/model/comment.rb**.

### Migra la base de datos

consola

```bash
rake db:migrate
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
por

```ruby
resources :posts do  
  resources :comments
end
```

### Para terminar con la lógica, creamos el controlador

```bash
rails g controller comments
```

El controlador de comentarios solo va a tener las acciones de crear y borrar comentarios

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

## Las vistas y los estilos de los comentarios

### DRY: Don't Repeat Yourself

El principio **No te repitas** (en inglés **Don't Repeat Yourself** ó **DRY**, también conocido como: Una vez y sólo una) es una filosofía de definición de procesos que promueve la reducción de la duplicación, especialmente en computación.

### Post parcial

Creamos un parcial para simplificar las vistas de `show` e `index`

Crea un nuevo archivo `_post.html.erb` en **app/views/posts/**

```rhtml
<div class="posts-wrapper">
  <div class="post">
    <div class="post-head">
      <div class="thumb-img"></div>
      <div class="user-name">
        <%= post.user.name %>
      </div>
    </div>
    <div class="image center-block">
      <%= link_to (image_tag post.image.url(:medium), class:'img-responsive'), post_path(post) %>
    </div>
    <div class="post-bottom">
      <div class="description">
        <div class="user-name">
          <%= post.user.name %>
        </div>
        <%= post.description %>
      </div>
      <% if post.comments %>
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
      <% end %>
    </div>
    <div class="comment-like-form row">
      <div class="like-button col-sm-1">
        <span class="glyphicon glyphicon-heart-empty"></span>
      </div>
      <div class="comment-form col-sm-11">
        <%= form_for [post, post.comments.new] do |f| %>
          <%= f.text_field :content, placeholder: 'Añade un comentario...' %>
        <% end %>
      </div>
    </div>
  </div>
</div>
```

Reemplaza **app/views/posts/show.html.erb**

```rhtml
<%= render 'post', post: @post %>
<% if @post.user.id == current_user.id %>
  <div class="text-center edit-links">
    <%= link_to "Cancelar", posts_path %>
    |
    <%= link_to "Editar el post", edit_post_path(@post) %>
  </div>
<% else %>
  <div class="text-center edit-links">
    <%= link_to "Cancelar", posts_path %>
  </div>
<% end %>
```

Y también reemplaza **app/views/posts/index.html.erb**

```rhtml
<% @posts.each do |post| %>
  <%= render 'post', post: post %>
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
  .image {
    border-bottom: 1px solid #eeefef;
    border-top: 1px solid #eeefef;
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

## El baile de Github

¡Ahora veremos en secuencia los pasos necesarios para subir tu primer proyecto a la plataforma Github!

1. En la parte superior derecha de tu espacio de trabajo en [C9](http://c9.io), haz clic en tu foto para abrir el panel de configuración y clic en `Dashboard`.
[https://c9.io/account/ssh](https://c9.io/account/ssh)
2. Ahora click en el círculo de arriba que tiene un engranaje y después en el menú lateral que dice `SSH keys`
3. Copia todas las lineas que empezan por `ssh-rsa...`
4. Crea una cuenta en GitHub: [https://github.com](https://github.com)
7. Entra en [tu perfil de usuario](https://github.com/settings/profile) y haz clicc en `SSH and GPG keys`.
[https://github.com/settings/ssh](https://github.com/settings/ssh)
8. Ahora Clic en “Add SSH Key”. Introduce el título: " C9 ", pega la clave SSH en el cuadro "key", y haz clic en "Add key".
9. Crea un repositorio nuevo vacío para tu nuevo proyecto. Desde tu repositorio, copia el enlace SSH. Por defecto GitHub muestra el enlace HTTPS; ¡tendrás que cambiarlo a ssh primero! Se verá algo como:
```
git@github.com:sunombre/nombredelproyecto.git
```
10. Convierte tu directorio actual en un repositorio git ejecutando en la consola de C9:
```
git init
```
11. Utilizando el enlace SSH que copiaste en el paso 9, añade el repositorio remoto como origen:
```
git remote add origin git@github.com:sunombre/nombredelproyecto.git
```
12. Añade tus archivos y haz commit
```
git add .
git commit -m "Mi Primer commit"
```
13. Sube los archivos:
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

por


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

por

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

por

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
