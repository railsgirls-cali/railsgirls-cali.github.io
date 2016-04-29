---
layout: inner
title: Foro
lead_text: Crea un Foro desde cero usando Rails 4 y MongoDB
permalink: /forum/
---

## Demo:
http://cali-coder-girls.herokuapp.com/

## 1. Crea una aplicación nueva

### Crea una nueva aplicación 

consola

```bash
$ rails new cali-coder-girls --skip-active-record --skip-bundle --skip-test-unit

$ cd cali-coder-girls
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
<h1>Foro Cali Coder Girls</h1>
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
<p>Este es mi primer foro</p>
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
``

## 6. Instalación Bootstrap

### Añade la gema de Bootstrap

**/Gemfile**

```ruby
gem 'bootstrap-sass'
```

### Las nuevas gemas se instalan con bundle install

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

### Vuelve a iniciar el servidor

consola

```
CONTROL + C
rails server
```

## 6. Añade elementos de Bootstrap a la página

### ¡Añade un contenedor a tu aplicación!

**views/layouts/application.html.erb**

```rhtml
<%= link_to "Home", root_path %>
<%= link_to "About", about_path %>
<div class="container">
  <% if notice %>
    <div class="alert alert-info alert-dismissible fade in" role="alert">
       <button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">×</span></button> 
       <p><%= notice %></p>
    </div>
  <%end%>
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
      <%= link_to "Cali Coder Girls", root_path, class: "navbar-brand" %>
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

### Añade el encabezado a la página de inicio

**views/pages/home.html.erb**

```rhtml
<div class="jumbotron">
  <h1>Foro Rails Girls Cali</h1>
  Haz clic aquí para <%= link_to "Registrar", "#", class: "btn btn-primary" %>
</div>
```
### Añadimos una clase "text-center" 

**/app/views/pages/home.html.erb**

```rhtml
<div class="jumbotron text-center">
  <h1>Foro Rails Girls Cali</h1>
  <p>
   <%= link_to "Iniciar sesion", "#", class: "btn btn-default btn-lg" %>
   <%= link_to "Registrar", "#", class: "btn btn-primary btn-lg" %>
  </p>    
</div>

```
### Personalizamos el encabezado con botones de autenticacion y algunas imagenes
**/app/views/pages/home.html.erb**

```rhtml
<div class='jumbotron text-center'>
  <h1>Foro Rails Girls Cali</h1>
  <%= link_to "Registrarse", "#", class: "btn btn-info btn-auth" %>
  <%= link_to "Iniciar Sesion", "#", class: "btn btn-info btn-auth" %>
</div>
<div class="container text-center">
  <div class='row banner'>
    <div class='col-xs-6 col-md-3'>
      <%=image_tag "image_2.png",class: "img-responsive banner-image" %>
    </div>
    <div class='col-xs-6 col-md-3'>
      <%=image_tag "image_1.png" ,class: "img-responsive banner-image"%>
    </div>
    <div class='col-xs-6 col-md-3'>
      <%=image_tag "image_1.png" ,class: "img-responsive banner-image"%>
    </div>
    <div class='col-xs-6 col-md-3'>
      <%=image_tag "image_2.png" ,class: "img-responsive banner-image"%>
    </div>
  </div>
  <p class='lead'>
    Use this document as a way to quickly start any new project.
    <br>
    All you get is this text and a mostly barebones HTML document.
  </p>
</div>

```
Los recursos se pueden descargar en el [link](https://drive.google.com/open?id=0B6wEtK9O5dmfNzlOT3hwcVpVdU0)

## 7. Mejoremos el diseño

### Personalizacion de Bootstrap

**app/assets/stylesheets/bootstrap_and_customization.css.scss**

```scss
@import url(https://fonts.googleapis.com/css?family=Roboto);

$body-bg:                          #fafafa !important;
$font-family-base:                  'Roboto', 'Helvetica Neue', Helvetica, Arial, sans-serif;
$navbar-height:                    80px;
$navbar-padding-vertical:          30px;
$navbar-default-bg:                #d3360b;
$navbar-default-brand-color:       white;
$navbar-default-link-color:        white;
$brand-primary:                    #e0330c;
$jumbotron-bg:                     white;
$btn-primary-bg:                   #D3360B;
$btn-primary-border:               darken($btn-primary-bg, 5%);
$btn-info-color:                   #D3360B;
$btn-info-bg:                      white;
$btn-info-border:                  darken($btn-primary-bg, 5%);
$alert-info-bg:                    white;
$alert-info-border:                #D3360B;
$alert-info-text:                  #D3360B;
@import 'bootstrap-sprockets';
@import 'bootstrap';

.navbar-brand {
  font-weight: bold;
}

.btn-auth{
  font-size: 18px;
  min-width: 180px;
  font-weight: bold;
}
.banner{
  margin: 40px 0 40px 0;
}

.banner-image{
  width: 200px;
  height: 200px;
}
```

## 8. Instalacion Mongoid

### Añadimos gemas 

**/Gemfile**

```ruby
  gem 'mongoid', '~> 5.1.0' 
  gem 'bson_ext'
```
consola

```bash
$ bundle install
```

### Generamos archivo de configuración de mongoid

```bash
  $ rails g mongoid:config
```
## 9. Crear scaffold para Topic

La herramienta  *scaffold* de rails permite generar facilmente versiones iniciales de modelos, controladores y vistas, tan solo con indicarle el nombre y los campos del modelo. Acontinuación creamos un scaffold para los Topics de nuestro foro

consola

```bash
  $ rails g scaffold Topic title:string description:string
```

##10. Añadimos el modulo *Timestamp* al modelo Topic

Este modulo permite acceder a los campos created_at y updated_at para nuestro modelo. De esta forma podremos saber cuando fue creado el Topic.

**app/models/topic.rb**

```ruby
  class Topic
    include Mongoid::Document
    include Mongoid::Timestamps
    field :title, type: String
    field :description, type: String
  end
```

## 10. Creamos un link para la vista de Topics

Por ahora utilizaremos el boton iniciar sesion para ver la lista de topicos 

En la vista **/app/views/pages/home.html.erb**

reemplazamos

```rhtml
  <%= link_to "Iniciar Sesion", "#", class: "btn btn-info btn-auth" %>
```
por 

```rhtml
  <%= link_to "Iniciar Sesion", topics_path, class: "btn btn-info btn-auth" %>
```

## 11. Modificamos la vista de Topics

Usamos bootstrap para personalizar la lista de topicos actuales, [aqui](http://bootsnipp.com/snippets/featured/bookmarks-reading-list) se pueden encontrar snippets que pueden reutilizarse en cualquiera de nuestras aplicaciones. 

reemplazamos el contenido de
**/app/views/topics/index.html.erb**
por:

```rhtml
<div class="container">
  <h1>Lista de Topics</h1>
  <p id="notice"><%= notice %></p>
  <div class="row">
    <div class="col-md-8">
      <% @topics.each do |topic| %>
        <%=link_to topic do %>
          <div class="well">
            <div class="col-xs-3 col-md-3 text-center">
                <%=image_tag "image_2.png", class: "img-rounded img-responsive"%>
            </div>
            <div class="col-xs-9 col-md-9 section-box">
                <h2>
                    <%= topic.title%>
                </h2>
                <p>
                    <%= topic.description%>
                </p>
                <p>
                  Por: <strong>Coder Girl</strong> - <%=topic.created_at.to_date%>
                </p>
                <hr />
                <div class="row rating-desc">
                    <div class="col-md-12">
                      <span class="glyphicon glyphicon-comment"></span>0 Posts
                      <div class="text-right">
                      </div>
                    </div>
                </div>
            </div>
          </div>
        <%end%>
      <% end %>
    </div>
    <div class="col-md-4">
      <%= link_to 'New Topic', new_topic_path %>
    </div>
  </div>
</div>

```
añadimos en
**app/assets/stylesheets/bootstrap_and_customization.css.scss**

```scss
.well{
  display: inline-block;
  width: 100%;
}
.well p{
  color: gray!important;
}
.glyphicon { margin-right:5px;}
.section-box h2 { margin-top:0px;}
.section-box h2 a { font-size:15px; }
.glyphicon-heart { color:#e74c3c;}
.glyphicon-comment { color:#27ae60;}
.separator { padding-right:5px;padding-left:5px; }
.section-box hr {margin-top: 0;margin-bottom: 5px;border: 0;border-top: 1px solid rgb(199, 199, 199);}
```

## 12. Añadimos un modal para crear Topics

Gracias a bootstrap podemos tener acceso a componentes que interactuan con el usuario mediante javascript. Acontinuacion usaremos un Modal o 'Popup' para crear un nuevo topic

En **app/views/topics/index.html.erb**

reemplazamos el link

```rhtml
  <%= link_to 'New Topic', new_topic_path %>
```
  por:

```rhtml
  <button type="button" class="btn btn-primary btn-lg" data-toggle="modal" data-target="#topicModal">
    Crear Topic
  </button>
```

### Creamos el parcial _form_new.html.erb para nuestro modal

**app/views/topics/_form_new.html.erb**

```rhtml
  <div class="modal fade" id="topicModal" tabindex="-1" role="dialog" aria-labelledby="topicModal">
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
          <h4 class="modal-title" id="myModalLabel">Nuevo Topic</h4>
        </div>
        <%=form_for @topic do |f|%>
          <div class="modal-body">
            <% if @topic.errors.any? %>
              <div id="error_explanation">
                <h2>
                  <%= "#{pluralize(@topic.errors.count, "error")} prohibited this topic from being saved:" %>
                </h2>
                <ul>
                  <% @topic.errors.full_messages.each do |msg| %>
                    <li>
                      <%= msg %>
                    </li>
                  <% end %>
                </ul>
              </div>
            <% end %>
            <div class="field">
              <%= f.text_field :title, placeholder: :title, class: 'form-control'%>
            </div>
            <br>
            <div class="field">
              <%= f.text_area :description, rows: 5 ,placeholder: :description, class: 'form-control'%>
            </div>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-default" data-dismiss="modal">Cerrar</button>
            <%=f.submit 'Guardar', class: 'btn btn-primary'%>
          </div>
        <%end%>
      </div>
    </div>
  </div>
```

### Añadimos el parcial a la vista de topics

Al final del archivo **app/views/topics/index.html.erb** añadimos lo siguiente:

```rhtml
...

<%=render "form_new"%>

```

### Añadimos la variable de instancia @topic en la acción index del controlador topics_controller

**app/controllers/topics/topics_controller.rb**

```ruby
...
  def index
    @topics = Topic.all
    @topic = Topic.new
  end
...
```
### Por último, redireccionamos a la lista de topics despues de creado un nuevo Topic 

reemplazamos la accion *create* del controlador **app/controllers/topics/topics_controller.rb**

```ruby
...
def create
  @topic = Topic.new(topic_params)
  respond_to do |format|
    if @topic.save
      format.html { redirect_to topics_path, notice: 'Se ha creado un nuevo Topic!' }
      format.json { render :show, status: :created, location: @topic }
    else
      format.html { render :new }
      format.json { render json: @topic.errors, status: :unprocessable_entity }
    end
  end
end
...
```

## 13. Organizamos la lista de Topics

Modificamos la acción index del controlador topics_controller para listar todos los topics ordenados del mas reciente al más antiguo

**app/controllers/topics/topics_controller.rb**


```ruby
...
  def index
    @topics = Topic.all.order_by(created_at: :desc)
    @topic = Topic.new
  end
...
``

## 14. Añadir Devise

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


### Crea las vistas de Devise

consola

```
rails g devise:views
```

## 15. Crea usuarios con Devise

### Crea un modelo de usuario

```
rails generate devise user
```

Esta línea de arriba crea un modelo de usuario y un nuevo archivo: **app/models/user.rb**

### Vuelve a iniciar el servidor

```
CONTROL + C (para parar el servidor)
rails server (para volver a iniciar el servidor)
```
Tendrás que reiniciar la aplicación cada vez que se instales una gema 


### Lista de rutas

```
rake routes
```

Muestra todas las rutas disponibles para tu aplicación. Podrás añadir más a lo largo del camino

### Modifica la vista de inicio

**app/views/pages/home.html.erb**

```rhtml
...
<div class='jumbotron text-center'>
  <h1>Foro Rails Girls Cali</h1>
  <%= link_to "Registrarse", new_user_registration_path, class: "btn btn-info btn-auth" %>
  <%= link_to "Iniciar Sesion", new_user_session_path, class: "btn btn-info btn-auth" %>
</div>
...
```

### Modifica el parcial de navegacíon

**app/views/layout/_header.html.erb**

```rhtml
...
<ul class="nav navbar-nav navbar-right">
  <% if user_signed_in? %>
    <li><%= link_to "Topics", topics_path %></li>
    <li>
      <%= link_to destroy_user_session_path, method: :delete do %>
        Salir
        <div class="glyphicon glyphicon-log-out"></div>
      <%end%>
    </li>
  <% else %>
    <li><%= link_to "Home", root_path %></li>
    <li><%= link_to "About", about_path %></li>
  <% end %>
</ul>
...
```
### Rederccionamos a la paina topics despues de iniciar sesion

Añadimos el siguiente metodo en **app/controllers/application_controller.rb**


```ruby
  def after_sign_in_path_for(resource)
    topics_path
  end
```
Ahora cada vez que se encuentre activa una sesion siempre se redrecciona a la vista de topics

### Modificamos la ruta raiz por defecto cuando alguien esta logeado

**config/routes.rb**
adicionar la ruta el siguiente codigo

```ruby
...
  authenticated :user do
      root :to => "topics#index", as: :authenticated_root
  end
  root "pages#home"
...
```

### Añadir un enlace de "Configuración de cuenta" al parcial de navegacíon

**app/views/layouts/_header.html.erb**

Debajo de `<li><%= link_to "Topics", topics_path %></li>`:

```rhtml
  ...
  <li><%= link_to "Configuración de cuenta", edit_user_registration_path %></li>
  ...
```

<li><%= link_to "Mi cuenta", edit_user_registration_path %></li>


## 16. Autorización : ¿Quién puede? Quién no puede?

### Actualizar el controlador Topics

Recursos: https://github.com/platafo Crearmatec/devise

Añadir `before_action` al Controlador Posts

**app/controllers/topics_controller.rb**

```ruby
before_action :authenticate_user!
```

## 17. Creamos asociaciones entre modelos. User - Topic

Recursos

asociacíon: http://guides.rubyonrails.org/association_basics.html


### Configure sus asociaciones

Un Topic belongs_to un Usuario

**app/models/post.rb**

```ruby
  class Topic

  ...
    belongs_to :user
  ...

  end
```

### Un usuario has_many Topics  

**app/models/user.rb**

```ruby
class User 
  
  ...
  has_many :topics
  ...

end
```

## 18. Asignamos un usuario a los topics creados

Modificamos la accion create del controlador **app/controllers/topics_controller.rb**

```ruby
  def create
    @topic = Topic.new(topic_params)
    @topic.user = current_user 
  
  ...
```

### Mostramos el email del usuario creado

**app/views/topics/index.html.haml**

reemplazamos

```rhtml
  <p>
    Por: <strong>Coder Girl</strong> - <%=topic.created_at.to_date%>
  </p>
```

por:

```rhtml
  <p>
    Por: <strong><%=topic.user.try(:email)%></strong> - <%=topic.created_at.to_date%>
  </p>
```
## 19. Ahora añadiremos nuestro último modelo llamado Post. 

consola 

```bash
  rails g scaffold Post body
```

añadimos el modulo *Timestamps* para el modelo Post
**app/models/post.rb **

```ruby
  ...
    include Mongoid::Timestamps
  ...
```

### Configure las asociaciones User - Topic - Post

Topic has_many Posts

añadimos en **app/models/topic.rb**

```ruby
  ...
    has_many :posts
  ...
```

User has_many Posts

añadimos en **app/models/user.rb**

```ruby
  ...
    has_many :posts
  ...
```

Post belongs_to Topics  
Post belongs_to User

añadimos en **app/models/post.rb**

```ruby
  ...
    belongs_to :user
    belongs_to :topic
  ...
```

## 20. Modificamos la vista para mostrar un Topic

Ahora vamos a mostrar los posts creados para cada Topic

reemplazamos el codigo en
**app/views/topics/show.html.erb**

```rhtml
  <div class="text-center"> 
    <%=link_to @topic do %>
      <h1>
        <strong><%= @topic.title %></strong>
      </h1>
    <%end%>
    <p>
      <strong>Description:</strong>
      <%= @topic.description %>
    </p>
      <%= link_to 'Edit', edit_topic_path(@topic) %> |
      <%= link_to 'Back', topics_path %>
  </div>
  <div class="container">
    <div class="row">
      <div class="col-md-8 col-md-offset-2">
        <h3 class="page-header">Posts</h3>
          <section class="post-list">
            <%@topic.posts.each do |post|%>
              <article class="row">
                <div class="col-md-2 col-sm-2 hidden-xs">
                  <figure class="thumbnail">
                    <img class="img-responsive" src="http://www.keita-gaming.com/assets/profile/default-avatar-c5d8ec086224cb6fc4e395f4ba3018c2.jpg" />
                    <figcaption class="text-center"><%=post.user.email%></figcaption>
                  </figure>
                </div>
                <div class="col-md-10 col-sm-10">
                  <div class="panel panel-default arrow left">
                    <div class="panel-body">
                      <header class="text-left">
                        <time class="post-date" datetime="16-12-2014 01:05"><i class="fa fa-clock-o"></i> <%=post.created_at.to_date%></time>
                      </header>
                      <div class="post-body">
                        <p>
                          <%=post.body%>
                        </p>
                      </div>
                    </div>
                  </div>
                </div>
              </article>
            <%end%>
          </section>
      </div>
    </div>
  </div>
```
añadimos estilos  **app/assets/stylesheets/bootstrap_and_customization.css.scss**

```scss

/*Post List styles*/
.post-list .row {
  margin-bottom: 0px;
}
.post-list .panel .panel-heading {
  padding: 4px 15px;
  position: absolute;
  border:none;
  /*Panel-heading border radius*/
  border-top-right-radius:0px;
  top: 1px;
}
.post-list .panel .panel-heading.right {
  border-right-width: 0px;
  /*Panel-heading border radius*/
  border-top-left-radius:0px;
  right: 16px;
}
.post-list .panel .panel-heading .panel-body {
  padding-top: 6px;
}
.post-list figcaption {
  /*For wrapping text in thumbnail*/
  word-wrap: break-word;
}
/* Portrait tablets and medium desktops */
@media (min-width: 768px) {
  .post-list .arrow:after, .post-list .arrow:before {
    content: "";
    position: absolute;
    width: 0;
    height: 0;
    border-style: solid;
    border-color: transparent;
  }
  .post-list .panel.arrow.left:after, .post-list .panel.arrow.left:before {
    border-left: 0;
  }
  /*****Left Arrow*****/
  /*Outline effect style*/
  .post-list .panel.arrow.left:before {
    left: 0px;
    top: 30px;
    /*Use boarder color of panel*/
    border-right-color: inherit;
    border-width: 16px;
  }
  /*Background color effect*/
  .post-list .panel.arrow.left:after {
    left: 1px;
    top: 31px;
    /*Change for different outline color*/
    border-right-color: #FFFFFF;
    border-width: 15px;
  }
  /*****Right Arrow*****/
  /*Outline effect style*/
  .post-list .panel.arrow.right:before {
    right: -16px;
    top: 30px;
    /*Use boarder color of panel*/
    border-left-color: inherit;
    border-width: 16px;
  }
  /*Background color effect*/
  .post-list .panel.arrow.right:after {
    right: -14px;
    top: 31px;
    /*Change for different outline color*/
    border-left-color: #FFFFFF;
    border-width: 15px;
  }
}
.post-list .post-body {
  margin-top: 6px;
}

.btn-create-post{
  margin-top: 20px;
  width: 200px;
}
```


## 20. Creacion de Posts

creamos el parcial **app/views/topics/_post_form.html.erb**

```rhtml
  <%= form_for(@new_post) do |f| %>
    <% if @new_post.errors.any? %>
      <div id="error_explanation">
        <h2><%= pluralize(@new_post.errors.count, "error") %> prohibited this post from being saved:</h2>
        <ul>
        <% @new_post.errors.full_messages.each do |message| %>
          <li><%= message %></li>
        <% end %>
        </ul>
      </div>
    <% end %>
    <div class="field">
      <%= f.text_area :body, rows: 5 ,placeholder: "Espacio para escribir el Post", class: 'form-control' %>
    </div>
    <%= f.hidden_field :topic_id, value: @topic.id %>
    <div class="actions text-right">
      <%= f.submit "Crear Post", class: 'btn btn-primary btn-create-post'%>
    </div>
  <% end %>
```
## Añadimos el parcial a la vista

**app/views/topics/show.html.erb**


```rhtml
  ...
    </section>
    <%=render "post_form"%>
  ...
```

## Definimos la variable @new_post en el controlador topics_controller

**app/controllers/topics_controller.rb**

```ruby
...
  def show
    @new_post = Post.new
  end
...
```

##  Modificamos el controlador posts_controllers

Se asigna el usuario actual para el post y se redicciona al topic al que pertenece

**app/controllers/posts_controller.rb**

```ruby
...
  def create
    @post = Post.new(post_params)
    @post.user = current_user
    @topic = Topic.find(post_params[:topic_id])
    
    respond_to do |format|
      if @post.save
        format.html { redirect_to @topic, notice: 'Post was successfully created.' }
        format.json { render :show, status: :created, location: @post }
      else
        format.html { render :new }
        format.json { render json: @post.errors, status: :unprocessable_entity }
      end
    end
  end
...
```

## Strong Paramteres

Recursos: https://github.com/rails/strong_parameters

Añadimos topic_id a la  lista de parametros permitidos por el formulario de posts
**app/controllers/posts_controller.rb**
 
```ruby
  def post_params
    params.require(:post).permit(:body,:topic_id)
  end
```

## 21. Visualizacion de numero de posts

Adicionamos el numero de post totales para el topic
**app/views/topics/show.html.erb**

```rhtml
...
  <h3 class="page-header"><%=@topic.posts.count%> Posts</h3>
...

```

De igual forma en el index de topics 

**app/views/topics/index.html.erb**

```rhtml
  ...
    <span class="glyphicon glyphicon-comment"></span><%=topic.posts.count%> Posts
  ...
```


## 23. Cambia las vistas de Devise

### Modifica el código para cada una de las vistas de Devise

**app/views/devise/registrations/new.html.erb**

```rhtml
  <div class="container">
    <div class="col-md-6 col-md-offset-3">
      <div class="panel panel-default ">
        <div class="panel-heading text-center"><h2>Regístrate</h2><p>Es gratis</p></div>
        <div class="panel-body">
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
              <%= f.submit "Regístrate", class: "btn btn-primary" %>
            </div>
            <%= render "devise/shared/links" %>
          <% end %>
        </div>
         <div class="container-fluid text-center">
          <%=image_tag "image_4.jpg", class: "img-"%>
         </div>
        <div class="panel-footer"></div>
      </div>
    </div>
  </div>
```

**app/views/devise/registrations/edit.html.erb**

```rhtml
<div class="container">
    <div class="col-md-10 col-md-offset-1">
      <div class="panel panel-default ">
        <div class="panel-heading"><h2>Mi Cuenta</h2></div>
        <div class="panel-body">
          <div class="row">
            <%= form_for(resource, as: resource_name, url: registration_path(resource_name), html: { method: :put }) do |f| %>
            <%= devise_error_messages! %>
            <div class="col-md-6">
              <div class="field">
                <%= f.label :email %><br />
                <%= f.email_field :email, autofocus: true, class: "form-control" %>
              </div>
              <% if devise_mapping.confirmable? && resource.pending_reconfirmation? %>
                <div>Currently waiting confirmation for: <%= resource.unconfirmed_email %></div>
              <% end %>
              <div class="field">
                <%= f.label :password %> <i>(leave blank if you don't want to change it)</i><br />
                <%= f.password_field :password, autocomplete: "off" , class: "form-control"%>
              </div>
              <div class="field">
                <%= f.label :password_confirmation %><br />
                <%= f.password_field :password_confirmation, autocomplete: "off" , class: "form-control"%>
              </div>
              <div class="field">
                <%= f.label :current_password %> <i>(we need your current password to confirm your changes)</i><br />
                <%= f.password_field :current_password, autocomplete: "off", class: "form-control" %>
              </div>
              <br>  
              <div class="actions">
                <%= f.submit "Update" , class: "btn btn-primary" %>
              </div>
            </div>
            <% end %>
            <div class="col-md-6">
              <h3>Cancel my account</h3>
              <p>Unhappy? <%= button_to "Cancel my account", registration_path(resource_name), data: { confirm: "Are you sure?" }, method: :delete %></p>
            </div>
          </div>            
        </div>
      </div>
    </div>
  </div>
```

**app/views/devise/sessions/new.html.erb**

```rhtml
<div class="container">
  <div class="col-md-6 col-md-offset-3">
    <div class="panel panel-default ">
      <div class="panel-heading text-center"><h2>Iniciar Sesion</h2></div>
      <div class="panel-body">
        <%= form_for(resource, as: resource_name, url: session_path(resource_name)) do |f| %>
          <div class="field">
            <%= f.label :email %><br />
            <%= f.email_field :email, autofocus: true ,class: "form-control"%>
          </div>
          <div class="field">
            <%= f.label :password %><br />
            <%= f.password_field :password, autocomplete: "off",class: "form-control" %>
          </div>
          <% if devise_mapping.rememberable? -%>
            <div class="field">
              <%= f.check_box :remember_me %>
              <%= f.label :remember_me %>
            </div>
          <% end %>
          <br>
          <div class="actions">
            <%= f.submit "Iniciar Sesion", class: "btn btn-primary" %>
          </div>
        <% end %>
      </div>
      <div class="panel-footer"><%= render "devise/shared/links" %></div>
    </div>
  </div>
</div>
```


