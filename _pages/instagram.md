---
layout: inner
title: Instagram
lead_text: Crea un clone de Instagram desde zero
permalink: /instagram/
---




## 1. Crea una aplicación nueva

### Crea una nueva aplicación Rails

consola

```
$ rails new instagram

$ cd instagram
```

### Arranca el servidor de Rails

consola

```
$ rails server
```


## 2. Página de inicio

En el navegador, ve a la URL: [localhost:3000](localhost:3000) . Esta es la página de inicio por defecto para las aplicaciones Rails.

### Crea una nueva página

consola

```
$ rails generate controller pages home
```

En tu navegador, ve a la URL : [localhost:3000/página/home](localhost:3000/página/home) y ve la nueva página en blanco que se acaba de crear.

### Actualiza el texto en la nueva página

**app/views/pages/home.html.erb**

```html
<h1>¡Bienvenidos a mi aplicación!</h1>
```

## 3. Crea la raíz de la aplicación

### Mostrar la página de inicio de tu aplicación

**config/routes.rb**

Reemplazar la linea

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

### Siempre corre bundle install para instalar una nueva gema

consola

```
$ bundle install
```

### Entender el documento Application.css

**app/assets/stylesheets/application.css**


### Crea un nuevo documento SCSS

**app/assets/stylesheets/bootstrap_and_customization.css.scss**

```scss
@import 'bootstrap';
```

### Vuelve a iniciar el servidor

consola

```
CONTROL + C
rails server
```

## 7. Añade elementos de Bootstrap a la página

### ¡Añade un contenedor a tu aplicación!

**views/layouts/application.html.erb**

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

### Importa la el Javascript para Bootstrap
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
	<h1>Bienvenido a mi aplicación!</h1>
	Haz clic aquí para <%= link_to "Registrar", "#", class: "btn btn-primary" %>
</div>
```

## 8. Personalizar Bootstrap

### Por ejemplo, actualicemos la barra de navegación

**app/views/layouts/_header.html.erb**

```html
<nav class="navbar navbar-default" role="navigation">
```

## 9. Mejoremos el diseño

### Cambios de estilo

**app/assets/stylesheets/bootstrap_and_customization.css.scss**

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
  <h1>Bienvenidos a mi aplicación!</h1>
  <p>
   <%= link_to "Iniciar sesion", "#", class: "btn btn-default btn-lg" %>
   <%= link_to "Registrar", "#", class: "btn btn-primary btn-lg" %>
  </p>    
</div>
```

### Cambia el enlace principal de la navegacíon de HTML a Ruby

**app/views/layouts/_header.html.erb**

```rhtml
<%= link_to "Instagram", root_path, class: "navbar-brand" %>
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

### Instalar Devise

```
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

```
rails generate devise user
```

Esta línea de arriba crea un modelo de usuario y un nuevo archivo: **app/models/user.rb**

Ve a **db/migration** y deberías tener en los archivos algo así como **db/migration/20130922022322_devise_create_users.rb**

El número es la fecha de creacíon

### Migra la base de datos

consola

```
rake db:migrate
```

Este comando toma el archivo de migración y lo ejecuta, de manera que genere tablas en la base de datos

### Vuelve a iniciar el servidor

```
CONTROL + C (para parar el servidor)
rails server (para volver a iniciar el servidor)
```

Tendrás que reiniciar la aplicación cada vez que se instales una gema o cada vez que ejecutes `rake db:migrate`

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
<ul class="nav navbar-nav navbar-right">
  <li><%= link_to "Home", root_path %></li>
  <li><%= link_to "About", about_path %></li>
  <% if user_signed_in? %>
    <li><%= link_to "Cerrar sesión", destroy_user_session_path, method: :delete %></li>
  <% else %>
    <li><%= link_to "Iniciar sesión", new_user_session_path %></li>
  <% end %>
</ul>
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
  <h1>Forgot your password?</h1>

  <%= form_for(resource, :as => resource_name, :url => password_path(resource_name), :html => { :method => :post }) do |f| %>
    <%= devise_error_messages! %>

    <div class="form-group">
      <%= f.label :email %>
      <%= f.email_field :email, class: "form-control", :autofocus => true %>
    </div>

    <div class="form-group">
      <%= f.submit "Send me reset password instructions", class: "btn btn-success" %>
    </div>
  <% end %>

  <%= render "devise/shared/links" %>

</div>
```

**app/views/devise/passwords/edit.html.erb**

```rhtml
<div class="form-wrapper">
  <h1>Change your password</h1>

  <%= form_for(resource, :as => resource_name, :url => password_path(resource_name), :html => { :method => :put }) do |f| %>
    <%= devise_error_messages! %>
    <%= f.hidden_field :reset_password_token %>

    <div class="form-group">
      <%= f.label :password, "New password" %>
      <%= f.password_field :password, class: "form-control", :autofocus => true %>
    </div>

    <div class="form-group">
      <%= f.label :password_confirmation, "Confirm new password" %>
      <%= f.password_field :password_confirmation %>
    </div>

    <div class="form-group">
      <%= f.submit "Change my password", class: "btn btn-success" %>
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
      <%= f.email_field :email, class: "form-control", :autofocus => true %>
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
      <%= f.submit "Sign in", class: "btn btn-success" %>
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

### Añadir un enlace de "Configuración de cuenta" al parcial de navegacíon

**app/views/layouts/_header.html.erb**

Debajo de `<% if user_signed_in? %>`:

```rhtml
<li><%= link_to "Configuración de cuenta", edit_user_registration_path %></li>

```

## 15. Generate Posts Scaffold

### Generate a posts scaffold

```
$ rails generate scaffold posts description:string
$ rake db:migrate #run the migration
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
      redirect_to @post, notice: 'Post was successfully created.'
    else
      render :new
    end
  end

  def update
    if @post.update(post_params)
      redirect_to @post, notice: 'Post was successfully updated.'
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
      <h2><%= pluralize(@post.errors.count, "error") %> prohibited this post from being saved:</h2>

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

### Añade un enlace para crear un nuevo post al navbar

**app/views/layouts/_header.html.erb**

Debajo de `<% if user_signed_in? %>`:

```rhtml
<li><%= link_to 'Nuevo post', new_post_path %></li>
```

## 18. Posts, Usuarios y asociacíon

Recursos

asociacíon: http://guides.rubyonrails.org/association_basics.html

### Configure sus asociaciones

Un Post belongs_to un Usuario

**app/models/post.rb**

```ruby
class Post < ActiveRecord::Base
	belongs_to :user
end
```


### Generar una nueva migración de índice de un usuario

```
$ rails generate migration add_user_id_to_posts user_id:integer:index
```


### Inicie la consola de Rails

La consola de Rails nos permite interactuar directamente con los datos en la base de datos . Usa la consola para actualizar directamente los datos  , o  sólo para probar el código Ruby antes de integrarlo a su proyecto

```
$ rails console
```

Una vez en la consola ...

```
> Post.connection #Esto establece una conexión con la base de datos ( y escupe una gran cantidad de datos innecesarios)
> Post.inspect #muestra todos los parámetros para un Post
> post = Post.first #Nos trae el primer Post asegurate que la primer letra es MAYÚSCULA
> post.user
```

Stop the Console when you're done

CONTROL + D #closes the Console

### Un usuario has_many Posts  

**app/models/user.rb**

```ruby
class User < ActiveRecord::Base
  # Include default devise modules. Others available are:
  # :token_authenticatable, :confirmable,
  # :lockable, :timeoutable and :omniauthable
  devise :database_authenticatable, :registerable,
         :recoverable, :rememberable, :trackable, :validatable

  has_many :posts
end
```


### A ver si funciono

De vuelta en la consola de Rails (en nuestra consola) vamos a configurar un ID de usuario en un Post.

```
> post = Post.first
> post #echar una mirada al post
> post.user_id = 1
> post.save

> user = User.first
> user.posts
```

## 19. Autorización : ¿Quién puede? Quién no puede?

### Actualizar el controlador Posts

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
      redirect_to @post, notice: 'Post was successfully created.'
    else
      render :new
    end
  end

  def update
    if @post.update(post_params)
      redirect_to @post, notice: 'Post was successfully updated.'
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
      redirect_to posts_path, notice: "Not authorized to edit this post" if @post.nil?
    end

    # Never trust parameters from the scary internet, only allow the white list through.
    def post_params
      params.require(:post).permit(:description, :image)
    end
end
```

### Add devise User authentication

Recursos: https://github.com/plataformatec/devise

Añadir `before_action` al Controlador Posts

**app/controllers/posts_controller.rb**

```ruby
before_action :authenticate_user!, except: [:index, :show]
```


### Add correct_user method

Add the `before_action` to your Posts Controller

**app/controllers/posts_controller.rb**

```ruby
before_action :correct_user, only: [:edit, :update, :destroy]
```

## 20. Image Upload with Paperclip

### Instalar el procesador de imagenes ImageMagick

En la consola

```
$ sudo apt-get install imagemagick
```

### Install the Paperclip gem

https://github.com/thoughtbot/paperclip

**/Gemfile**

```ruby
gem 'paperclip', '~> 4.2'
```

Then run:

```
$ bundle install
```

**/app/models/post.rb**

```ruby
class Post < ActiveRecord::Base
  belongs_to :user
  has_attached_file :image, :styles => { :medium => "640x", :thumb => "100x100>" }
  validates_attachment_content_type :image, :content_type => /\Aimage\/.*\Z/
end
```

### Generate a paperclip migration

```
$ rails generate paperclip post image
```

Run and check the migration

```
$ rake db:migrate
$ rake db:migrate:status
```

### Volver a iniciar el servidor after adding a gem file

```
$ CONTROL + C
$ rails server
```

### Edit the post form
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

### Update the Posts Controller for strong parameters

**/app/controllers/concerns/posts_controller.rb**

```ruby

.
  def post_params
    params.require(:post).permit(:description, :image)
  end
.

```

### Update the posts index

**/app/views/posts/index.html.erb**

```rhtml
<div class="posts-wrapper row">
  <% @posts.each do |post| %>
    <div class="post">
      <div class="post-head">
        <div class="name">
          <%= pin.user.email if pin.user %>
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

### Delete posts made by non users

```shell
$ rails console
$ Post.first
$ post = Post.first
$ post.destroy
$ Post.first.destroy
```

### Update the posts show view

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

**app/assets/stylesheets/bootstrap_and_customization.css.scss**

```css
.edit-links {
  margin-top: 20px;
  margin-bottom: 40px;
}
```

y en **app/views/posts/show.html.erb**, lo mas arriba añade

```rhtml
<div class="text-center">
  <%= image_tag @post.image.url(:medium) %>
</div>
```

### Y si queremos borrar nuestro post?

**app/views/posts/show.html.erb**

Completamente abajo colocamos:

```rhtml
<div class="text-center edit-links">
  <%= link_to "Borrar Post", post_path(@post), method: :delete, data: { confirm: "Esta segura que quieres eliminar este post?" } %>
  |
  <%= link_to "cancelar", posts_path %>
</div>
```

## Añade un nombre de usuario para personalizar la aplicacíon

### Crea la migracion en base de datos

consola

```shell
$ rails generate migration AddNameToUsers name:string
```

### Migra la base de datos

consola

```shell
$ rake db:migrate
```

### Añade al fomulario de registro el campo nombre  

**app/views/devise/registrations/edit.html.erb**

```rhtml
.
     <div class="form-group">
       <%= f.label :name %>
       <%= f.text_field :name, class: "form-control", :autofocus => true %>
     </div>
.
```

### Indica a Devise autorizar este nuevo parametro  

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

### Y tambien agregamos el campo en las vistas

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

Crear el archivo **app/controllers/registrations_controller.rb**:

```ruby
class RegistrationsController < Devise::RegistrationsController

  private

  def sign_up_params
    params.require(:user).permit(:email, :user_name, :password, :password_confirmation)
  end

  def account_update_params
    params.require(:user).permit(:email, :user_name, :password, :password_confirmation, :current_password)
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

## Proteger su posts

### Rodea el enlace de edición con un "si " condicional

De esta manera sólo se puede ver tus posts . Para poner esto de otra manera: Un usuario sólo puede ver sus posts (y no los posts de otros usuarios ) . ¿Tiene algun sentido?


**app/views/posts/show.html.erb**

```rhtml
<% if post.user == current_user %>
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

### Proteger los posts tambien desde el controlador

**app/controllers/posts_controller.rb**

```ruby
private

def owned_post  
  unless current_user == @post.user
    flash[:alert] = "That post doesn't belong to you!"
    redirect_to root_path
  end
end
```

Despues inserte un before_action en la parte superior del controlador , especificando el método owned_post solamente para las acciones de edición , actualización y destruir.

```ruby
before_action :owned_post, only: [:edit, :update, :destroy]
```

## Añadir la posibilidad de comentar nuestros posts
