---
layout: inner
title: Pinterest
lead_text: Crear un clone de Pinterest desde zero
permalink: /pinterest/
---




## 1. Crear una aplicacíon nueva

### Crea una nueva applicacion Rails

consola

```
$ rails new pinteresting

$ cd pinteresting
```

### Arranca el servidor de Rails

consola

```
$ rails server
```


## 2. Pagina de inicio

En el navegador , vaya a la URL: [localhost:3000](localhost:3000) . Esta es la página de inicio por defecto para las aplicaciones Rails .

### Crear una nueva pagina

consola

```
$ rails generate controller pages home
```

En su navegador , vaya a la URL : [localhost:3000/página/home](localhost:3000/página/home) y ver la nueva página en blanco que acaba de crear .

### Actualizar el texto en la nueva pagina

**app/views/pages/home.html.erb**

```
<h1>Bienvenidos a mi aplicación!</h1>
```

## 3. Crear la raiz de la aplicacion

### Mostrar la página de inicio de su aplicación

**config/routes.rb**

Reemplazar la linea

```
get "pages/home"
```

...por:

```
root "pages#home"
```

## 4. Crear mas paginas

### Añadir una nueva acción en el controlador

**app/controllers/pages_controller.rb**

```
def about
end
```

###  Crear el código HTML en la vista

**app/views/pages/about.html.erb**

```
<h1>Quien somos</h1>
<p>Estamos trabajando en nuestra  Pinteresting aplicación</p>
```

###  Agregar la routa

**config/routes.rb**

```
get "about" => "pages#about"
```

## 5. Embedded Ruby?

### Cambiar el enlace HTML a un enlace inbebido de ruby
**app/views/pages/home.html.erb**

```erb
<%= link_to "here", "#" %>
```

En HTML, un enlace es el siguiente

`` `
<a href="#"> aquí </a>
`` `

Estos son etiquetas de Ruby

`` `
< % = % >
`` `

En Ruby on Rails un enlace se verá así

```erb
<%= link_to "aquí", "#" %>
```

## 6. Instalar Bootstrap

### Añadir la gema de Bootstrap

**/Gemfile**

```
gem 'bootstrap-sass'
```

### Siempre bundle install para instalar una nueva gema

consola

```
$ bundle install
```

### Entender el documento Application.css

**app/assets/stylesheets/application.css**


### Crear un nuevo documento SCSS

**app/assets/stylesheets/bootstrap_and_customization.css.scss**

```
@import 'bootstrap';
```

### Volver a iniciar el servidor

consola

```
CONTROL + C
$ rails server
```

## 7. Añadir elementos de Bootstrap a la pagina

### Añadir un contenedor a su aplicación!

**views/layouts/application.html.erb**

```rhtml
<%= link_to "Home", root_path %>
<%= link_to "About", about_path %>
<div class="container">
    <%= yield %>
</div>
```

### Crear un parcial de encabezado

Crear el archivo **app/views/layouts/_header.html.erb**

### Crear un enlace al parcial

**app/views/layouts/application.html.erb**

Despues del `<body>`

```
<%= render 'layouts/header' %>
```

### Add the nav bar

**app/views/layouts/_header.html.erb**

```
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
      <a class="navbar-brand" href="#">Pinteresting</a>
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

### Require Bootstrap's JavaScript
**app/assets/javascripts/application.js**

```
...
//= require jquery
//= require jquery_ujs
//= require bootstrap-sprockets
//= require turbolinks
//= require_tree .
```

### Añadir viewport
**views/layouts/application.html.erb**

Despues del `<head>` y antes del `<title>`.

Insertar:

```
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### Añadir el intitulado a la página de inicio

**views/pages/home.html.erb**

```
<div class="jumbotron">
	<h1>Bienvenido a mi aplicación!</h1>
	Haz clic aquí para <%= link_to "Registrar", "#", class: "btn btn-primary" %>
</div>
```

## 8. Personalizar Bootstrap

### Por ejemplo , actualizar la barra de navegación

**app/views/layouts/_header.html.erb**

```
<nav class="navbar navbar-inverse navbar-default" role="navigation">
```

## 9. Mejorar el diseño

### Cambios de estilo

**app/assets/stylesheets/bootstrap_and_customization.css.scss**

```
@import url(http://fonts.googleapis.com/css?family=Lato:400,700);

$body-bg:                          #ecf0f1;
$font-family-sans-serif:           'Lato', 'Helvetica Neue', Helvetica, Arial, sans-serif;
$navbar-height:                    45px;
$navbar-default-bg:                white;
$navbar-default-brand-color:       #c0392b;
$brand-primary:                    #c0392b;
$jumbotron-bg:                     white;

@import 'bootstrap-sprockets';
@import 'bootstrap';

.center {
     text-align: center;
}

.navbar-brand {
     font-weight: bold;
}
```


### Añadir una clase "center" y botón "Iniciar sesion"

**/app/views/pages/home.html.erb**

```
<div class="jumbotron center">
  <h1>Bienvenidos a mi aplicación!</h1>
  <p>
   <%= link_to "Iniciar sesion", "#", class: "btn btn-default btn-lg" %>
   <%= link_to "Registrar", "#", class: "btn btn-primary btn-lg" %>
  </p>    
</div>
```

### Cambiar el enlace principal de la navegacíon de HTML a Ruby

**app/views/layouts/_header.html.erb**

```
<%= link_to "Pinteresting", root_path, class: "navbar-brand" %>
```

## 10. Añadir Devise

### Añadir la gema de Devise

**/Gemfile**

```
gem 'devise'
```

consola

```
$ bundle install
```

### Instalar Devise

```
$ rails generate devise:install
```

## 11. Configuración de Devise

### URLs por defecto

**config/environments/development.rb**

```
config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
```

**config/environments/production.rb**

```
config.action_mailer.default_url_options = { host:    'http://pinteresting-commits.herokuapp.com/' }
```


### Mensajes flash

Los mensajes flash son los mensajes en sitios web que dicen " Gracias por registrar en " o "Gracias por suscribirse a "

**app/views/layouts/application.html.erb**

```
<div class="container">

  <% flash.each do |name, msg| %>
     <%= content_tag(:div, msg, class: "alert alert-#{name}") %>
  <% end %>

  <%= yield %>

</div>
```

### Set precompile to "false"

**config/application.rb**

```
config.assets.initialize_on_precompile = false
```

### Crear las vistas de Devise

consola

```
$ rails g devise:views
```

## 12. Crear usuarios con Devise

### Crear un modelo de usuario

```
$ rails generate devise user
```

Esta línea de arriba crea un modelo de usuario y un nuevo archivo: **app/models/user.rb**

Go to **db/migration** y deberias tener en los archivos algo así como **db/migration/20130922022322_devise_create_users.rb** # El número es la fecha de creacíon

### Migrar la base de datos

consola

```
$ rake db:migrate
```

Este comando toma el archivo de migración y lo ejecuta , de manera que genere tablas en la base de datos

### Volver a iniciar el servidor

```
CONTROL + C para parar el servidor
$ rails server # para volver a iniciar el servidor
```

Tendrá que reiniciar la aplicación cada vez que se instala una gema o cada vez que se ejecuta `$rake db:migrate`

## 13. Registrar nuevos usuarios o iniciar sesíon

```
$ rake routes
```

Muestra todas las rutas disponibles para su aplicación . Podrás añadir más a lo largo del camino

### Modificar la vista de inicio

**app/views/pages/home.html.erb**

```
<div class="jumbotron center">
 <h1>Bienvenidos a mi aplicación!</h1>
 <% if user_signed_in? %>
      # haz algo
 <% else %>
   <p>
     <%= link_to "Iniciar sesíon", new_user_session_path, class: "btn btn-default btn-lg" %>
     <%= link_to "Registrar", new_user_registration_path, class: "btn btn-primary btn-lg" %>
   </p>
  <% end %>  
</div>
```

### Modificar el parcial de navegacíon

**app/views/layout/_header.html.erb**

```
<ul class="nav navbar-nav navbar-right">
  <li><%= link_to "Home", root_path %></li>
  <li><%= link_to "About", about_path %></li>
  <% if user_signed_in? %>
    <li><%= link_to "Cerrar sesíon", destroy_user_session_path, method: :delete %></li>
  <% else %>
    <li><%= link_to "iniciar sesíon", new_user_session_path %></li>
  <% end %>
</ul>
```

## 14. Cambiar las vistas de Devise

### Modifica el codigo para cada una de las vistas de Devise

**app/views/devise/registrations/new.html.erb**

```
<div class="panel panel-default">
  <div class="panel-heading">
    <h1>Registrar</h1>
  </div>

  <div class="panel-body">
    <%= form_for(resource, :as => resource_name, :url => registration_path(resource_name)) do |f| %>
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
        <%= f.submit "Registrar", class: "btn btn-primary" %>
      </div>
    <% end %>
  </div>

  <div class="panel-footer">
    <%= render "devise/shared/links" %>
  </div>
</div>
```

**app/views/devise/registrations/edit.html.erb**

```
<div class="panel panel-default">
  <div class="panel-heading">
    <div class="panel-title">
      <h1>Edit <%= resource_name.to_s.humanize %></h1>
    </div>
  </div>
  <div class="panel-body">
    <%= form_for(resource, :as => resource_name, :url => registration_path(resource_name), :html => { :method => :put }) do |f| %>
      <%= devise_error_messages! %>

      <div class="form-group">
        <%= f.label :email %>
        <%= f.email_field :email, class: "form-control", :autofocus => true %>
      </div>

      <div class="form-group">
        <%= f.label :password %> <i>(leave blank if you don't want to change it)</i>
        <%= f.password_field :password, class: "form-control", :autocomplete => "off" %>
      </div>

      <div class="form-group">
        <%= f.label :current_password %> <i>(we need your current password to confirm your changes)</i>
        <%= f.password_field :current_password, class: "form-control" %>
      </div>

      <div class="form-group">
        <%= f.submit "Update", class: "btn btn-primary" %>
      </div>
    <% end %>
  </div>
  <div class="panel-footer">
    <h3>Cancel my account</h3>

    <p>Unhappy? <%= button_to "Cancel my account", registration_path(resource_name), :data => { :confirm => "Are you sure?" }, :method => :delete, class: "btn btn-warning" %></p>

    <%= link_to "Back", :back %>
  </div>
</div>
```

**app/views/devise/passwords/new.html.erb**

```
<div class="panel panel-default">
  <div class="panel-heading">
    <div class="panel-title">
      <h1>Forgot your password?</h1>
    </div>
  </div>
  <div class="panel-body">
    <%= form_for(resource, :as => resource_name, :url => password_path(resource_name), :html => { :method => :post }) do |f| %>
      <%= devise_error_messages! %>

      <div class="form-group">
        <%= f.label :email %>
        <%= f.email_field :email, class: "form-control", :autofocus => true %>
      </div>

      <div class="form-group">
        <%= f.submit "Send me reset password instructions", class: "btn btn-primary" %>
      </div>
    <% end %>
  </div>
  <div class="panel-footer">
    <%= render "devise/shared/links" %>
  </div>
</div>
```

**app/views/devise/passwords/edit.html.erb**

```
<div class="panel panel-default">
  <div class="panel-heading">
    <div class="panel-title">
      <h1>Change your password</h1>
    </div>
  </div>
  <div class="panel-body">
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
        <%= f.submit "Change my password", class: "btn btn-primary" %>
      </div>
    <% end %>
  </div>
  <div class="panel-footer">
    <%= render "devise/shared/links" %>
  </div>
</div>
```

**app/views/devise/sessions/new.html.erb**

```
<div class="panel panel-default">
  <div class="panel-heading">
    <div class="panel-title">
      <h1>Sign in</h1>
    </div>
  </div>
  <div class="panel-body">
    <%= form_for(resource, :as => resource_name, :url => session_path(resource_name)) do |f| %>

      <div class="form-group">
        <%= f.label :email %>
        <%= f.email_field :email, class: "form-control", :autofocus => true %>
      </div>

      <div class="form-group">
        <%= f.label :password %>
        <%= f.password_field :password, class: "form-control" %>
      </div>

      <div class="form-group">
        <div class="checkbox">
          <%= f.check_box :remember_me %>
          <%= f.label :remember_me %>
        </div>
      </div>

      <div class="form-group">
        <%= f.submit "Sign in", class: "btn btn-primary" %>
      </div>
    <% end %>
  </div>
  <div class="panel-footer">
    <%= render "devise/shared/links" %>
  </div>
</div>
```

### Añadir un enlace de "Configuración de cuenta" al parcial de navegacíon

**app/views/layouts/_header.html.erb**

```
.
.
.
<li><%= link_to "Configuración de cuenta", edit_user_registration_path %></li>
.
.
.
```

## 15. Generate Pins Scaffold

### Generate a pins scaffold

```
$ rails generate scaffold pins description:string
$ rake db:migrate #run the migration
```


## 16. Simplificando el controlador de Pins

**app/controllers/pins_controller.rb**

```
class PinsController < ApplicationController
  before_action :set_pin, only: [:show, :edit, :update, :destroy]

  def index
    @pins = Pin.all
  end

  def show
  end

  def new
    @pin = Pin.new
  end

  def edit
  end

  def create
    @pin = Pin.new(pin_params)
    if @pin.save
      redirect_to @pin, notice: 'Pin was successfully created.'
    else
      render :new
    end
  end

  def update
    if @pin.update(pin_params)
      redirect_to @pin, notice: 'Pin was successfully updated.'
    else
      render :edit
    end
  end

  def destroy
    @pin.destroy
    redirect_to pins_url
  end

  private
    # Use callbacks to share common setup or constraints between actions.
    def set_pin
      @pin = Pin.find(params[:id])
    end

    # Never trust parameters from the scary internet, only allow the white list through.
    def pin_params
      params.require(:pin).permit(:description)
    end
end
```

## 17. Las vistas de pins

### Esto se llama el parcial "formulario"

**apps/views/pins/new.html.erb**

```
<%= render 'form' %>
```

**apps/views/pins/_form.html.erb**

```
<%= form_for(@pin) do |f| %>
  <% if @pin.errors.any? %>
    <div id="error_explanation">
      <h2><%= pluralize(@pin.errors.count, "error") %> prohibited this pin from being saved:</h2>

      <ul>
      <% @pin.errors.full_messages.each do |msg| %>
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

## 18. Pins, Usuarios y asociacíon

Recursos

asociacíon: http://guides.rubyonrails.org/association_basics.html

### Configure sus asociaciones

Un Pin belongs_to un Usuario

**app/models/pin.rb**

```
class Pin < ActiveRecord::Base
	belongs_to :user
end
```


### Generar una nueva migración de índice de un usuario

```
$ rails generate migration add_user_id_to_pins user_id:integer:index
```


### Inicie la consola de Rails

La consola de Rails nos permite interactuar directamente con los datos en la base de datos . Usa la consola para actualizar directamente los datos  , o  sólo para probar el código Ruby antes de integrarlo a su proyecto

```
$ rails console
```

Una vez en la consola ...

```
> Pin.connection #Esto establece una conexión con la base de datos ( y escupe una gran cantidad de datos innecesarios)
> Pin.inspect #muestra todos los parámetros para un Pin
> pin = Pin.first #Nos trae el primer Pin asegurate que la primer letra es MAYÚSCULA
> pin.user
```

Stop the Console when you're done

CONTROL + D #closes the Console

### Un usuario has_many Pins  

**app/models/user.rb**

```
class User < ActiveRecord::Base
  # Include default devise modules. Others available are:
  # :token_authenticatable, :confirmable,
  # :lockable, :timeoutable and :omniauthable
  devise :database_authenticatable, :registerable,
         :recoverable, :rememberable, :trackable, :validatable

  has_many :pins
end
```


### A ver si funciono

De vuelta en la consola de Rails (en nuestra consola) vamos a configurar un ID de usuario en un Pin.

```
> pin = Pin.first
> pin #ecahr una mirada al pin
> pin.user_id = 1
> pin.save

> user = User.first
> user.pins
```

## 19. Autorización : ¿Quién puede? Quién no puede?

### Actualizar del controlador Pins

**app/controllers/pins_controller.rb**

```
class PinsController < ApplicationController
  before_action :set_pin, only: [:show, :edit, :update, :destroy]

  def index
    @pins = Pin.all
  end

  def show
  end

  def new
    @pin = current_user.pins.build
  end

  def edit
  end

  def create
    @pin = current_user.pins.build(pin_params)
    if @pin.save
      redirect_to @pin, notice: 'Pin was successfully created.'
    else
      render :new
    end
  end

  def update
    if @pin.update(pin_params)
      redirect_to @pin, notice: 'Pin was successfully updated.'
    else
      render :edit
    end
  end

  def destroy
    @pin.destroy
    redirect_to pins_url
  end

  private
    # Use callbacks to share common setup or constraints between actions.
    def set_pin
      @pin = Pin.find_by(id: params[:id])
    end

    def correct_user
      @pin = current_user.pins.find_by(id: params[:id])
      redirect_to pins_path, notice: "Not authorized to edit this pin" if @pin.nil?
    end

    # Never trust parameters from the scary internet, only allow the white list through.
    def pin_params
      params.require(:pin).permit(:description, :image)
    end
end
```

### Update the pins view

**app/views/pins/index.html.erb**

```
<%= pin.user.email if pin.user %>
```

### Add devise User authentication

Recursos: https://github.com/plataformatec/devise

Añadir before_action al Controlador Pins

**app/controllers/pins_controller.rb**

```
before_action :authenticate_user!, except: [:index, :show]
```

### Surround the edit link with an "if" conditional

This way you can only see your pins. To put that another way: A user can only see his pins (and not other user's pins). Make sense?

**app/views/pins/index.html.erb**

```
...
<% if pin.user == current_user %>
  <%= link_to 'Edit', edit_pin_path(pin) %>
  <%= link_to 'Destroy', pin, method: :delete, data: { confirm: 'Are you sure?' } %>
<% end %>
...
```

**app/views/pins/show.html.erb**

```
...
<% if @pin.user == current_user %>
  <%= link_to 'Edit', edit_pin_path(@pin) %>
<% end %>
<%= link_to 'Back', pins_path %>
...
```

### Add correct_user method

Add the before_action to your Pins Controller

**app/controllers/pins_controller.rb**

before_action :correct_user, only: [:edit, :update, :destroy]

### Surround the "New Pin" link with an "if" conditional

**app/views/pins/index.html.erb**

```
...
<% if user_signed_in? %>
  <%= link_to 'New Pin', new_pin_path %>
<% end %>
...
```

## Paperclip ImageMagick Install


## 20. Image Upload with Paperclip

### Instalar el procesador de imagenes

En la consola

```
$ sudo apt-get install imagemagick
```

### Install the paperclip gem

https://github.com/thoughtbot/paperclip

**/Gemfile**

```
gem 'paperclip', '~> 4.2'
```

Then run:

```
$ bundle install
```

**/app/models/pin.rb**

```
class Pin < ActiveRecord::Base
  belongs_to :user
  has_attached_file :image, :styles => { :medium => "300x300>", :thumb => "100x100>" }
  validates_attachment_content_type :image, :content_type => /\Aimage\/.*\Z/
end
```

### Generate a paperclip migration

```
$ rails generate paperclip pin image
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

### Edit the pin form
**/app/views/pins/_form.html.erb**

```
<%= form_for @pin, html: { multipart: true } do |f| %>
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

### Update the Pins Controller for strong parameters

**/app/controllers/concerns/pins_controller.rb**

```
.
.
.
    def pin_params
      params.require(:pin).permit(:description, :image)
    end
.
.
.
```

### Update the pins show view

**/app/views/pins/show.html.erb**
```

<%= image_tag @pin.image.url %>
.
.
.
```

### Update the pins index

**/app/views/pins/index.html.erb**

```
<h1>Listing pins</h1>

<table>
  <thead>
    <tr>
      <th>Image</th>
      <th>Description</th>
      <th>User</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>

  <tbody>
    <% @pins.each do |pin| %>
      <tr>
        <td><%= image_tag pin.image.url(:medium) %></td>
        <td><%= pin.description %></td>
        <td><%= pin.user.email if pin.user %></td>
        <td><%= link_to 'Show', pin_path(pin) %></td>
        <% if pin.user == current_user %>
          <td><%= link_to 'Edit', edit_pin_path(pin) %></td>
          <td><%= link_to 'Destroy', pin, method: :delete, data: { confirm: 'Are you sure?' } %></td>
        <% end %>
      </tr>
    <% end %>
  </tbody>
</table>

<br>
<% if user_signed_in? %>
  <%= link_to 'New Pin', new_pin_path %>
<% end %>
```

### Delete pins made by non users

```
$ rails console
$ Pin.first
$ pin = Pin.first
$ pin.destroy
$ Pin.first.destroy
```

### Update the pins show view for image size

**/app/views/pins/show.html.erb**

```
<%= image_tag @pin.image.url(:medium) %>
```

## 21. Styling the pins with Masonry

### Add the Masonry and Turbolinks gems  

**/Gemfile**

```
gem 'jquery-turbolinks'
gem 'masonry-rails', '~> 0.2.0'
```

### Bundle  
consola

```
$ bundle install
```

### Modify our application.js file

**/app/assets/javascripts/application.js**

```
.
.
//= require masonry/jquery.masonry
//= require masonry/jquery.imagesloaded.min
```


### Modify our application.css file  

**/app/assets/stylesheets/application.css**

```
.
.
.
 *= require 'masonry/transitions'
```

### Update our Pins Index

**/app/views/pins/index.html.erb**

```
<div id="pins">
  <% @pins.each do |pin| %>
    <div class="box">
      <%= image_tag pin.image.url(:medium) %>
      <%= pin.description %>
      <%= pin.user.email if pin.user %>
      <%= link_to 'Show', pin_path(pin) %>
      <% if pin.user == current_user %>
        <%= link_to 'Edit', edit_pin_path(pin) %>
        <%= link_to 'Destroy', pin, method: :delete, data: { confirm: 'Are you sure?' } %>
      <% end %>
    </div>
  <% end %>
</div>
```

### Adding Pins directly from the header  

**/app/views/layouts/_header.html.erb**


```
.
.
.
  <li><%= link_to 'New Pin', new_pin_path %></li>
.
.
.
```

### Update our Pins stylesheet for Masonry CSS

**/app/assets/stylesheets/pins.css.scss**

```
.
.
#pins {
  margin: 0 auto;
}

.box {
  margin: 5px;
  width: 214px;
}

.box img {
  width: 100%;
}
```

### Update our Pins JavaScript for Masonry

**/app/assets/javascripts/pins.js.coffee**

```
.
.
$ ->
  $('#pins').imagesLoaded ->
    $('#pins').masonry
      itemSelector: '.box'
      isFitWidth: true
```

### Modify our application.js file for jQuery Turbolinks  

**/app/assets/javascripts/application.js**

```
//= require jquery.turbolinks
```

### Update our Pins Index for transitions and styling  

**/app/views/pins/index.html.erb**

```
<div id="pins" class="transitions-enabled">
  <% @pins.each do |pin| %>
    <div class="box panel panel-default">
      <%= image_tag pin.image.url(:medium) %>
      <div class="panel-body">
        <%= pin.description %>
        <%= pin.user.email if pin.user %>
        <%= link_to 'Show', pin_path(pin) %>
        <% if pin.user == current_user %>
          <%= link_to 'Edit', edit_pin_path(pin) %>
          <%= link_to 'Destroy', pin, method: :delete, data: { confirm: 'Are you sure?' } %>
        <% end %>
      </div>
    </div>
  <% end %>
</div>
```
