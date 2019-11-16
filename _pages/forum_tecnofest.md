---
layout: inner
title: Foro Tecnofest
lead_text: Todas las mujeres pueden aprender a programar
permalink: /forum_tecnofest/
---

## Repositorio Inicial:
https://github.com/davidvanegas7/forum-ror.git

## Nota 0:

Esta guia es una version reducida del foro, pensando en realizarlo para un entorno de 45 minutos. En este caso, el proyecto ya viene con un controlador inicial "pages" y preconfigurado con bootstrap.

## 1. Crea el entorno

### ¡Vamos a crear una nueva cuenta en [www.codeanywhere.com](https://www.codeanywhere.com)!

Una vez te registres, recibiras un correo con un link de verificación. Es necesario verificar la cuenta para poder utilizar las acciones del entorno.

## 2. Configuración del entorno

En la ventana "Connection Wizard" seleccionamos la opcion "Git from URL" y pegamos el link del repositorio https://github.com/davidvanegas7/forum-ror.git

Presionamos Next.

En el nombre del entorno ponemos "Foro" y en el stack buscamos "Firehose" el cual tiene por defecto la configuracion de Ruby on Rails.

Al final presionamos Create y esperamos un par de minutos.

## 3. Ajustes finales al entorno

En la lista de la izquierda, presionamos click derecho sobre Foro y luego SSH Terminal. Esto nos abre una terminal de Unix ubicados en el directorio del proyecto.

Escribimos uno por uno:

```
bundle install
```

Con este comando instalaremos todos los paquetes del proyecto definidos en el archivo Gemfile.

### Nota 1: 

Cada vez que sea necesario ejecutar el proyecto para visualizarlo, es necesario ejecutar el servidor en la ip 0.0.0.0 con el comando:

```
rails s -b 0.0.0.0
```

### Nota 2: 

Estas son etiquetas de Ruby

```erb
< % = % >
```

Para escribir enlaces en Ruby utilizamos la expresion: 

```rhtml
<%= link_to "aqui", "#" %>
```

Lo cual nos imprime en HTML, un enlace es así

```html
<a href="#"> aqui </a>
```

### 4. Crea un parcial de encabezado

Crea el archivo **app/views/layouts/_header.html.erb** y añade la barra de navegación

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

### Crea un enlace al parcial

En el archivo **app/views/layouts/application.html.erb**

Después del `<body>` agregar

```erb
<%= render 'layouts/header' %>
```

Esta instrucción añade el encabezado a todas las páginas

### Personalizamos el Home con botones de autenticación y algunas imagenes
**/app/views/pages/home.html.erb**

```rhtml
<div class='jumbotron text-center'>
  <h1>Foro Rails Girls Cali</h1>
  <%= link_to "Regístrate", "#", class: "btn btn-info btn-auth" %>
  <%= link_to "Iniciar Sesión", "#", class: "btn btn-info btn-auth" %>
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
</div>

```
Los recursos se pueden descargar en el [link](https://drive.google.com/open?id=0B6wEtK9O5dmfNzlOT3hwcVpVdU0) y debe subirse a la carpeta **app/assets/images**.

## 5. Instalación Mongoid

### Generamos el archivo de configuración de mongoid

```bash
rails g mongoid:config
```
## 6. Crea el scaffold para Topic

La herramienta  *scaffold* de rails permite generar fácilmente versiones iniciales de modelos, controladores y vistas, tan solo con indicarle el nombre y los campos del modelo. A continuación, creamos un scaffold para los Topics de nuestro foro

consola

```bash
rails g scaffold Topic title:string description:string
```

##10. Añadimos el módulo *Timestamp* al modelo Topic

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

## 7. Creamos un link para la vista de Topics

Por ahora utilizaremos el botón iniciar sesión para ver la lista de tópicos

En la vista **/app/views/pages/home.html.erb**

reemplazamos

```rhtml
  <%= link_to "Iniciar Sesión", "#", class: "btn btn-info btn-auth" %>
```
por

```rhtml
  <%= link_to "Iniciar Sesión", topics_path, class: "btn btn-info btn-auth" %>
```

## 8. Modificamos la vista de Topics

Usamos bootstrap para personalizar la lista de tópicos actuales, [aquí](http://bootsnipp.com/snippets/featured/bookmarks-reading-list) se pueden encontrar snippets que pueden reutilizarse en cualquiera de nuestras aplicaciones.

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
**app/assets/stylesheets/bootstrap_and_customization.scss**

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

## 9. Añadimos un modal para crear Topics

Gracias a bootstrap podemos tener acceso a componentes que interactúan con el usuario mediante Javascript.
A continuación usaremos un Modal o 'Popup' para crear un nuevo topic

En **app/views/topics/index.html.erb**

reemplazamos el link

```rhtml
  <%= link_to 'Nuevo Topic', new_topic_path %>
```
  por:

```rhtml
  <button type="button" class="btn btn-primary btn-lg" data-toggle="modal" data-target="#topicModal">
    Crear Topic
  </button>
```

### Creamos el parcial `_form_new.html.erb` para nuestro modal

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
                  <%= "#{pluralize(@topic.errors.count, "error")} no permitieron guardar este topic:" %>
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

<%= render "form_new" %>

```

### Añadimos la variable de instancia `@topic` en la acción index del controlador `topics_controller`

**app/controllers/topics/topics_controller.rb**

```ruby
...
  def index
    @topics = Topic.all
    @topic = Topic.new
  end
...
```
### Por último, redireccionamos a la lista de topics después de creado un nuevo Topic

reemplazamos la acción *create* del controlador **app/controllers/topics/topics_controller.rb**

```ruby
...
def create
  @topic = Topic.new(topic_params)
  respond_to do |format|
    if @topic.save
      format.html { redirect_to topics_path, notice: '¡Se ha creado un nuevo Topic!' }
      format.json { render :show, status: :created, location: @topic }
    else
      format.html { render :new }
      format.json { render json: @topic.errors, status: :unprocessable_entity }
    end
  end
end
...
```

## 10. Organizamos la lista de Topics

Modificamos la acción index del controlador `topics_controller` para listar todos los topics ordenados del más reciente al más antiguo

**app/controllers/topics/topics_controller.rb**


```ruby
...
  def index
    @topics = Topic.all.order_by(created_at: :desc)
    @topic = Topic.new
  end
...
```

## 11. Añadir Devise

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

## 12. Crea usuarios con Devise

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
Tendrás que reiniciar la aplicación cada vez que instales una gema


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
  <%= link_to "Regístrate", new_user_registration_path, class: "btn btn-info btn-auth" %>
  <%= link_to "Iniciar Sesión", new_user_session_path, class: "btn btn-info btn-auth" %>
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
### Redireccionamos a la página topics después de iniciar sesión

Añadimos el siguiente método en **app/controllers/application_controller.rb**


```ruby
  def after_sign_in_path_for(resource)
    topics_path
  end
```
Ahora cada vez que se encuentre activa una sesión, siempre se redirecciona a la vista de topics

### Modificamos la ruta raíz por defecto cuando alguien esté logeado

**config/routes.rb**
Adiciona a la ruta el siguiente código

```ruby
...
  authenticated :user do
      root :to => "topics#index", as: :authenticated_root
  end
  root "pages#home"
...
```

### Añade un enlace de "Configuración de cuenta" al parcial de navegación

**app/views/layouts/_header.html.erb**

Debajo de `<li><%= link_to "Topics", topics_path %></li>`:

```rhtml
  ...
  <li><%= link_to "Configuración de cuenta", edit_user_registration_path %></li>
  ...
```

<li><%= link_to "Mi cuenta", edit_user_registration_path %></li>


## 13. Autorización : ¿Quién puede? ¿Quién no puede?

### Actualizar el controlador Topics

Recursos: https://github.com/platafo Crearmatec/devise

Añadir `before_action` al Controlador Posts

**app/controllers/topics_controller.rb**

```ruby
before_action :authenticate_user!
```

## 14. Creamos asociaciones entre modelos. User - Topic

Recursos

asociacíon: http://guides.rubyonrails.org/association_basics.html


### Configura tus asociaciones

Un Topic `belongs_to` un Usuario

**app/models/post.rb**

```ruby
  class Topic

  ...
    belongs_to :user
  ...

  end
```

### Un usuario `has_many` Topics  

**app/models/user.rb**

```ruby
class User

  ...
  has_many :topics
  ...

end
```

## 15. Asignamos un usuario a los topics creados

Modificamos la acción `create` del controlador **app/controllers/topics_controller.rb**

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
## 16. Ahora añadiremos nuestro último modelo llamado Post.

consola

```bash
rails g scaffold Post body
```

añadimos el modulo *Timestamps* para el modelo Post
**app/models/post.rb**

```ruby
  ...
    include Mongoid::Timestamps
  ...
```

### Configure las asociaciones User - Topic - Post

Topic `has_many` Posts

añadimos en **app/models/topic.rb**

```ruby
  ...
    has_many :posts
  ...
```

User `has_many` Posts

añadimos en **app/models/user.rb**

```ruby
  ...
    has_many :posts
  ...
```

Post `belongs_to` Topics  
Post `belongs_to` User

añadimos en **app/models/post.rb**

```ruby
  ...
    belongs_to :user
    belongs_to :topic
  ...
```

## 17. Modificamos la vista para mostrar un Topic

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
      <%= link_to 'Editar', edit_topic_path(@topic) %> |
      <%= link_to 'Volver', topics_path %>
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
añadimos estilos en  **app/assets/stylesheets/bootstrap_and_customization.scss**

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


## 17. Creación de Posts

creamos el parcial **app/views/topics/_post_form.html.erb**

```rhtml
  <%= form_for(@new_post) do |f| %>
    <% if @new_post.errors.any? %>
      <div id="error_explanation">
        <h2><%= pluralize(@new_post.errors.count, "error") %> no permitieron almacenar este post:</h2>
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
    <%= render "post_form" %>
  ...
```

## Definimos la variable `@new_post` en el controlador topics_controller

**app/controllers/topics_controller.rb**

```ruby
...
  def show
    @new_post = Post.new
  end
...
```

##  Modificamos el controlador `posts_controllers`

Se asigna el usuario actual para el post y se redirecciona al topic al que pertenece

**app/controllers/posts_controller.rb**

```ruby
...
  def create
    @post = Post.new(post_params)
    @post.user = current_user
    @topic = Topic.find(post_params[:topic_id])

    respond_to do |format|
      if @post.save
        format.html { redirect_to @topic, notice: '¡Post creado satisfactoriamente!' }
        format.json { render :show, status: :created, location: @post }
      else
        format.html { render :new }
        format.json { render json: @post.errors, status: :unprocessable_entity }
      end
    end
  end
...
```

## Strong Parameters

Recursos: https://github.com/rails/strong_parameters

Añadimos `topic_id` a la  lista de parámetros permitidos por el formulario de posts
**app/controllers/posts_controller.rb**

```ruby
  def post_params
    params.require(:post).permit(:body, :topic_id)
  end
```

## 18. Visualización de número de posts

Adicionamos el número de posts totales para el topic
**app/views/topics/show.html.erb**

```rhtml
...
  <h3 class="page-header"><%= @topic.posts.count %> Posts</h3>
...

```

De igual forma, en el index de topics

**app/views/topics/index.html.erb**

```rhtml
  ...
    <span class="glyphicon glyphicon-comment"></span><%= topic.posts.count %> Posts
  ...
```


## 19. Cambia las vistas de Devise

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
                <%= f.label :current_password %> <i>(Necesitamos tu contraseña actual para confirmar tus cambios)</i><br />
                <%= f.password_field :current_password, autocomplete: "off", class: "form-control" %>
              </div>
              <br>  
              <div class="actions">
                <%= f.submit "Actualizar" , class: "btn btn-primary" %>
              </div>
            </div>
            <% end %>
            <div class="col-md-6">
              <h3>Cancelar mi cuenta</h3>
              <p>Unhappy? <%= button_to "Cancelar mi cuenta", registration_path(resource_name), data: { confirm: "¿Estás segura?" }, method: :delete %></p>
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
      <div class="panel-heading text-center"><h2>Iniciar Sesión</h2></div>
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
            <%= f.submit "Iniciar Sesión", class: "btn btn-primary" %>
          </div>
        <% end %>
      </div>
      <div class="panel-footer"><%= render "devise/shared/links" %></div>
    </div>
  </div>
</div>
```
