---
layout: inner
title: Railslack
lead_text: Crea un clon de Slack desde cero
permalink: /slack/
---

<div class="repo">
  <h3>Repostitorio de la aplicación</h3>
  <a href="https://github.com/railsgirls-cali/example-railslack">
    https://github.com/railsgirls-cali/example-railslack</a>
</div>

## CONVENCIONES

1. consola

```
$
```

2. Modificación de archivos


```
[...]
test
[...]
```


## 1. Instala la última versión disponible de Ruby on Rails
Rails es un framework de ruby para desarrollar aplicaciones web, a pesar de estar compuesto de multiples librerias, Rails es en si mismo una gema de ruby.

*"Las gemas en Ruby son las bibliotecas o paquetes (código Ruby empaquetado de una manera predeterminada) de software que se instalan en el sistema para aumentar las funcionalidades del interprete"*.

Para instalar Rails debemos hacer lo siguiente:

```
$ gem install rails
```

Este proceso podría tomar unos minutos...

## 2. Crea una aplicación nueva
### Creando la aplicación
Una vez la gema esté instalada, vamos a proceder a crear nuestra aplicación bajo el nombre de **railslack-app**

```
$ rails new railslack-app
```

Una vez finalizado el proceso de generación de la nueva aplicación, será creada una carpeta con el nombre de la misma.

### Arrancando el servidor
Para poder arrancar el servidor y modificar la aplicación debemos ingresar a la carpeta creada.

```
$ cd railslack-app
```

Una vez dentro, debemos digitar la siguiente instrucción que iniciará nuestro servidor

```
$ rails server -b 0.0.0.0 -p 8080
```

El comando anterior usa las siguientes opciones:

- **-b** *especifíca que el servidor será accesible desde clientes externos, en este caso desde la internet utilizando cualquier navegador web si estás usando c9*
- **-p** *especifíca el puerto en el cual el servidor abre la conexión*

### Página de inicio

En cualquier navegador de tu computador escribe la URL: [localhost:3000](localhost:3000). Esta es la página de inicio por defecto para las aplicaciones Rails.

**NOTA** Si estás usando c9 no vas a poder acceder a la página de inicio en tu explorador usando la URL anterior, necesitas una URL especial, para el caso del taller la URL será genrada de la siguiente forma:

http://railslack-**your_id**-railsgirlscali.c9users.io/

## 3. Instala devise y bootstrap

### Configurando Boostrap

La mayoria de las aplicaciones web necesitan que los usuarios puedan crear una cuenta, modificar su perfil, iniciar y cerrar sesión. En el contexto de rails hay una gema que se integra naturalmente con él y gestiona estos componentes; esta gema se llama devise.

Ademas de instalar devise, para agilizar el proceso de creacion de estilos, utilizaremos un framework CSS, HTML y JS muy popular llamado bootstrap; este lo instalamos en forma de gema. Para eso abrimos el archivo `config/Gemfile` y copiamos lo siguiente:

```
[...]
gem 'devise'
gem 'bootstrap', '~> 4.0.0.alpha6'
[...]
```

En consola ejecutaremos el siguiente comando, para instalar nuestras nuevas gemas:

```
$ bundle install
```

Una vez instalado Bootstrap en nuestra aplicación, crearemos un nuevo documento SASS en `app/assets/stylesheets/bootstrap_and_overrides.sass` para importar todas las funcionalidades CSS de boostrap a nuestro proyecto. En este nuevo documento debemos añadir lo siguiente:

```
@import "bootstrap";
```

Igualmente, en el archivo `app/assets/javascripts/application.js` debemos agregar el código de abajo para importar todas las funcionalidades JS de Boostrap en nuestro proyecto.

```
[...]
//= require bootstrap
[...]
```

### Configurando Devise

En consola ejecuta los siguientes comandos para instalar devise, generar un modelo llamado User y generar las vistas para la personalización del manejo de sesiones de usuario.


```
$ rails generate devise:install
$ rails generate devise User
$ rails generate devise:views
$ rails db:migrate
```

Ahora restringe el acceso a todas las paginas del sitio solo para usuarios autenticados, para hacerlo debemos ingresar al archivo `app/controllers/application_controller.rb` y añadir lo siguiente:

```
[...]
before_action :authenticate_user!
[...]
```

## 4. Chat Rooms

El siguiente paso es agregar el soporte para las salas de chat (*chat rooms*), para eso genera el siguiente modelo.

en consola, digita lo siguiente:

```
$ rails g model ChatRoom title:string user:references
$ rails db:migrate
```

Una sala de chat debe tener un creador. Asegurate de establecer un relación de unos a muchos entre `chat_rooms` y `users`, es decir entre salas de chat y usuarios

De esta forma en el archivo `app/models/chat_room.rb`, cerciórate que este la siguiente línea de código, la cual denota una dependencia relacional entre los dos modelos.

```
[...]
belongs_to :user
[...]
```

Igualmente en el archivo `app/models/users.rb` agrega la linea de abajo para cerrar con la dependencia relacional que se creo en el modelo `chat_room`

```
[...]
has_many :chat_rooms, dependent: :destroy
[...]
```

Crea un controlador de salas de chat llamado `ChatRoomsController` en el archivo `app/controllers/chat_rooms_controller.rb`, en el cual deberás añadir el siguiente código para listar y crear salas de chat.

```
class ChatRoomsController < ApplicationController
  def index
    @chat_rooms = ChatRoom.all
  end

  def new
    @chat_room = ChatRoom.new
  end

  def create
    @chat_room = current_user.chat_rooms.build(chat_room_params)
    if @chat_room.save
      flash[:success] = 'Chat room added!'
      redirect_to chat_rooms_path
    else
      render 'new'
    end
  end

  private

  def chat_room_params
    params.require(:chat_room).permit(:title)
  end
end
```

Ahora crea el siguiente directorio `app/views/chat_rooms/` donde internamente crearás las siguientes vistas.

***index.html.erb***

```
<h1>Chat rooms</h1>

<p class="lead"><%= link_to 'New chat room', new_chat_room_path, class: 'btn btn-primary' %></p>

<ul>
  <%= render @chat_rooms %>
</ul>
```

***_chat_room.html.erb***

```
<li><%= link_to "Enter #{chat_room.title}", chat_room_path(chat_room) %></li>
```

***new.html.erb***
```
<h1>Add chat room</h1>

<%= form_for @chat_room do |f| %>
  <div class="form-group">
    <%= f.label :title %>
    <%= f.text_field :title, autofocus: true, class: 'form-control' %>
  </div>

  <%= f.submit "Add!", class: 'btn btn-primary' %>
<% end %>
```
## 5. Mensajes
### Modelos

La principal característica de nuestra aplicación es, por supuesto, un mensaje de chat. Estos deben pertenecer tanto a un usuario como a una sala de chat. Vamos a crear un modelo `Message` para definir la abstracción de un mensaje.

Para hacerlo, en consola, escribe lo siguiente:
```
$ rails g model Message body:text user:references chat_room:references
$ rails db:migrate
```

Ahora asegurate de establecer las relaciones adecuadas:

En el archivo `app/models/chat_room.rb` cerciórate que las siguientes líneas existan:

```
[...]
belongs_to :user
has_many :messages, dependent: :destroy
[...]
```

En el archivo `app/models/message.rb` cerciórate que las siguientes líneas existan:
```
[...]
belongs_to :user
belongs_to :chat_room
[...]
```

Finalmente, en el archivo `app/models/users.rb` añade las siguientes líneas:
```
[...]
has_many :chat_rooms, dependent: :destroy
has_many :messages, dependent: :destroy
[...]
```

### Controladores

Los mensajes deberian mostrarse cuando un usuario ingrese a una sala de chat, asi que crea una acción `show` en el controlador `app/controllers/chat_rooms_controller.rb`

```
[...]
def show
  @chat_room = ChatRoom.includes(:messages).find_by(id: params[:id])
end
[...]
```

**Nota:** el  método [includes](http://api.rubyonrails.org/classes/ActiveRecord/QueryMethods.html#method-i-includes) usado es para generar un proceso de 'eager loading' y evitar consultas N+1

### Vistas

Ahora crea las siguientes vistas:

***app/views/chat_rooms/show.html.erb***
```
<h1><%= @chat_room.title %></h1>

<div id="messages">
  <%= render @chat_room.messages %>
</div>
```

***app/views/messages/_message.html.erb***
```
<div class="card">
  <div class="card-block">
    <div class="row">
      <div class="col-md-1">
        <%= gravatar_for message.user %>
      </div>
      <div class="col-md-11">
        <p class="card-text">
          <span class="text-muted"><%= message.user.name %> at <%= message.timestamp %> says</span><br>
          <%= message.body %>
        </p>
      </div>
    </div>
  </div>
</div>
```

### Helpers y atributos virtuales

En este parcial se emplean tres nuevos métodos `user.name`, `message.timestamp` y `gravatar_for`.

Para definir un nombre de usuario simplemente eliminamos la parte del dominio del correo electrónico. De esta forma en el archivo `app/models/user.rb` añadimos el siguiente método:

```
[...]
def name
  email.split('@')[0]
end
[...]
```

El método `timestamp` se basa en el método `strftime` para presentar la fecha de creación del mensaje de manera amigable. Así, en el archivo `app/models/message.rb` dedemos añadir lo siguiente:

```
[...]
def timestamp
  created_at.strftime('%H:%M:%S %d %B %Y')
end
[...]
```

Finalmente, `gravatar_for` es un **helper** para mostrar tu imagen de usuario registrada en [gravatar](http://es.gravatar.com/). En el archivo `app/helpers/application_helper.rb` copia lo siguiente:

```
module ApplicationHelper
  def gravatar_for(user, opts = {})
    opts[:alt] = user.name
    image_tag "https://www.gravatar.com/avatar/#{Digest::MD5.hexdigest(user.email)}?s=#{opts.delete(:size) { 40 }}",
              opts
  end
end
```

### Estilos

Ahora agregamos un poco de estilos CSS (*usando SASS*) al contenedor de mensajes, para esto debemos crear el archivo `app/assets/stylesheets/main.sass` con las siguientes reglas de estilo:

```
#messages
  max-height: 450px
  overflow-y: auto
  .avatar
    margin: 0.5rem
```

### Configuración de rutas

Finalmente, debemos configurar las rutas de acceso a la aplicación editando el archivo `config/routes.rb`, para esto debemos añadir las siguientes líneas en el mismo:

```
[...]
resources :chat_rooms, only: [:new, :create, :show, :index]
root 'chat_rooms#index'
[...]
```

## 6. Agregando ActionCable

### Client Side

Para continuar, vamos a implementar un  `Service Broker`, que básicamente es una manera de establecer un canal de comunicación asincronicamente; podriamos decir que es un Servicio Postal, el cual utilizamos para poder enviar cartas a una persona que se encuentra lejos. Para esto vamos a instalar Redis, un motor de base de datos en memoria.

En el archivo *Gemfile* pega lo siguiente:

```
[...]
gem 'redis', '~> 3.2'
[...]
```

y ejecuta en consola el siguiente comando:
```
$ bundle install
```

Ahora modifica el archivo `config/cable.yml` para usar Redis como un adaptador:


```
[...]
adapter: redis
url: YOUR_URL
[...]
```

O simplemente usa `adapter: async` (valor por defecto).

Agrega en tu archivo `config/routes.rb` lo siguiente:


```
[...]
mount ActionCable.server => '/cable'
[...]
```


Revisa si el archivo `app/assets/javascripts/cable.js` contiene lo siguiente:

```
//= require action_cable
//= require_self
//= require_tree ./channels

(function() {
  this.App || (this.App = {});

  App.cable = ActionCable.createConsumer();

}).call(this);
```

Este archivo debe ser requerido dentro de `app/assets/javascripts/application.js`

```
[...]
//= require cable
[...]
```

Un `Consumer` (consumidor) es un cliente de una conexión web socket que puede suscribirse a uno o multiples canales. Cada servidor ActionCable puede manejar multiples conexiones. Un `channel` (canal)  es similar a un controlador MVC y es usado para `streaming`. Tu puedes leer mas acerca de la terminología de ActionCable [aqui](https://github.com/rails/rails/tree/master/actioncable#terminology).


Asi que vamos a crear un nuevo canal, para eso creamos el siguiente archivo `app/javascripts/channels/rooms.coffee`


```
App.global_chat = App.cable.subscriptions.create {
    channel: "ChatRoomsChannel"
    chat_room_id: ''
  },
  connected: ->
    # Called when the subscription is ready for use on the server

  disconnected: ->
    # Called when the subscription has been terminated by the server

  received: (data) ->
    # Data received

  send_message: (message, chat_room_id) ->
    @perform 'send_message', message: message, chat_room_id: chat_room_id
```

Básicamente lo que hacemos aqui, es suscribir un consumidor a `ChatRoomsChannel` y pasamos el id actual del la sala (En este punto realmente no pasamos nada, pero eso se arreglará pronto). La suscripción tiene un numero de callbacks autoexplicativos `connected`, `disconnected`, y `received`. Además, la suscripción define una función principal (`send_message`) que invoca un metodo con el mismo nombre del servidor y le pasa los datos necesarios.

Por supuesto, necesitamos un formulario para permitir que los usuarios envíen sus mensajes:

`app/views/chat_rooms/show.html.erb`

```
<%= form_for @message, url: '#' do |f| %>
  <div class="form-group">
    <%= f.label :body %>
    <%= f.text_area :body, class: 'form-control' %>
    <small class="text-muted">From 2 to 1000 characters</small>
  </div>

  <%= f.submit "Post", class: 'btn btn-primary btn-lg' %>
<% end %>
```

La variable de instancia `@message` debe estar en el método `show` del controlador `app/controllers/chat_rooms_controller.rb`
```
[...]
def show
  @chat_room = ChatRoom.includes(:messages).find_by(id: params[:id])
  @message = Message.new
end
[...]
```

Ahora agregamos algunas validaciones para los mensajes, esto lo hacemos en:

`app/models/message.rb`
```
[...]
validates :body, presence: true, length: {minimum: 2, maximum: 1000}
[...]
```

Y fijamos el id del chat-room con ayuda del atributo `data` de HTML

`app/views/chat_rooms/show.html.erb`
```
[...]
<div id="messages" data-chat-room-id="<%= @chat_room.id %>">
  <%= render @chat_room.messages %>
</div>
[...]
```

Habiendo hecho esto, podemos agregar el id del chat-room en el script.

Actualiza el archivo
`app/javascripts/channels/rooms.coffee`
```
jQuery(document).on 'turbolinks:load', ->
  messages = $('#messages')
  if $('#messages').length > 0

    App.global_chat = App.cable.subscriptions.create {
        channel: "ChatRoomsChannel"
        chat_room_id: messages.data('chat-room-id')
      },
      connected: ->
        # Called when the subscription is ready for use on the server

      disconnected: ->
        # Called when the subscription has been terminated by the server

      received: (data) ->
        # Data received

      send_message: (message, chat_room_id) ->
        @perform 'send_message', message: message, chat_room_id: chat_room_id
```

Nota: La parte de `jQuery(document).on 'turbolinks:load'`. Solo deberia hacerse si tu estas utilizando [Turbolinks](https://github.com/turbolinks/turbolinks-classic) 5 que soporta este nuevo evento.....

La lógica del script es muy simple: revisa si hay un bloque `#messages` en la página y si lo hay, se suscribe al canal de donde proviene el id del salón. El siguiente paso es escuchar el evento `submit` del formulario.

`app/javascripts/channels/rooms.coffee`
```
jQuery(document).on 'turbolinks:load', ->
  messages = $('#messages')
  if $('#messages').length > 0

    App.global_chat = App.cable.subscriptions.create
    # ...

    $('#new_message').submit (e) ->
      $this = $(this)
      textarea = $this.find('#message_body')
      if $.trim(textarea.val()).length > 1
        App.global_chat.send_message textarea.val(), messages.data('chat-room-id')
        textarea.val('')
      e.preventDefault()
      return false
```

Cuando el formulario es enviado, toma el cuerpo del mensaje, revisa que su longitud sea mayor que uno y llama la función `send_message` para transmitir el mensaje a todos los visitantes de la sala (`chat-room`).

### Server Side

Nuestra siguiente tarea será introducir un canal en nuestro servidor. En Rails 5, hay un  directorio llamado `channels` para alojarlos.
Crearemos el siguiente archivo `app/channels/chat_rooms_channel.rb` y pegamos lo siguiente:

```
class ChatRoomsChannel < ApplicationCable::Channel
  def subscribed
    stream_from "chat_rooms_#{params['chat_room_id']}_channel"
  end

  def unsubscribed
    # Any cleanup needed when channel is unsubscribed
  end

  def send_message(data)
    # process data sent from the page
  end
end
```
`subscribed` es un método especial para iniciar la transmisión desde un canal con un nombre dado. Mientras tengamos varias salones, el nombre del canal variará. Recuerda que nosotros proveemos `chat_room_id: messages.data('chat-room-id')` cuando se suscriben a un canal en nuestro script. Gracias a esto chat_room_id puede ser buscado dentro del método `subscribed` llamando `params['chat_room_id'].`

`unsubscribed` es una callback que se activa cuando se detiene el streaming, pero en esta guía no lo usaremos

El último método `send_message` se dispara cuando ejecutamos `@perform 'send_message', message: message, chat_room_id: chat_room_id` desde nuestro script. La variable `data` contiene un `hash` (colección de datos) de los datos enviados, por ejemplo, para acceder al mensaje tu deberías escribir `data['message']`.

Hay múltiples maneras para transmitir el mensaje recibido....

Primero que todo, modifica el método `send_message`

`app/channels/chat_rooms_channel.rb`

```
[...]
def send_message(data)
  current_user.messages.create!(body: data['message'], chat_room_id: data['chat_room_id'])
end
[...]
```

Una vez recibimos un mensaje se guarda en la base de datos; no necesitamos revisar que la sala de chat (`chat-room`) donde proviene exista, por defecto, en Rails 5, debe existir un registro padre para guardarlo. Este comportamiento puede ser cambiado estableciendo `optional: true` por la relación `belongs_to` (Lee acerca de los cambios en Rails 5 [aqui](https://www.sitepoint.com/onwards-to-rails-5-additions-changes-and-deprecations/))

Sin embargo hay un problema, el método de devise `current_user` no esta disponible para nosotros aqui. Para arreglar esto modificamos el archivo `connection.rb`  ubicado en el directorio `application_cable`

`app/channels/application_cable/connection.rb`

```
module ApplicationCable
  class Connection < ActionCable::Connection::Base
    identified_by :current_user

    def connect
      self.current_user = find_verified_user
      logger.add_tags 'ActionCable', current_user.email
    end

    protected

    def find_verified_user # this checks whether a user is authenticated with devise
      if verified_user = env['warden'].user
        verified_user
      else
        reject_unauthorized_connection
      end
    end
  end
end
```

Después de realizar esto, además de tener el metodo `current_user` disponible para el canal, ahora los usuarios que no estén autenticados no podrán transmitir sus mensajes.

El llamado a `logger.add_tags 'ActionCable', current_user.email` es usado para mostrar información de depuración en la consola. Por lo que podra ver algo similar a esto

```
[ActionCable] [test@example.com] Registered connection (Z2lkOi8vY2FibGUtY2hhdC9Vc2VyLzE)
[ActionCable] [test@example.com] ChatRoomsChannel is transmitting the subscription confirmation
[ActionCable] [test@example.com] ChatRoomsChannel is streaming from chat_rooms_1_channel
```

Under the hood Devise uses...

Ahora vamos agregar un callback que se activa después de que el mensaje se guarda en la base de datos, programando un job(Explicación)

***app/models/message.rb***
```
[...]
after_create_commit { MessageBroadcastJob.perform_later(self) }
[...]
```

In this callback self is a saved message, so we basically pass it to the job. Write the job now:

***app/jobs/message_broadcast_job.rb***
```
class MessageBroadcastJob < ApplicationJob
  queue_as :default

  def perform(message)
    ActionCable.server.broadcast "chat_rooms_#{message.chat_room.id}_channel",
                                 message: 'MESSAGE_HTML'
  end
end
```

The perform method does the actual broadcasting...

***app/jobs/message_broadcast_job.rb***
```
class MessageBroadcastJob < ApplicationJob
  queue_as :default

  def perform(message)
    ActionCable.server.broadcast "chat_rooms_#{message.chat_room.id}_channel",
                                 message: render_message(message)
  end

  private

  def render_message(message)
    MessagesController.render partial: 'messages/message', locals: {message: message}
  end
end
```

Para que esto funcione, debemos crear un controladro vacío:

***app/controllers/messages_controller.rb***

```
class MessagesController < ApplicationController
end
```

### Back to the Client Side

Great, now the server side is ready and we can finalize our script. As long as we broadcast HTML markup, it can be simply placed right onto the page without any further manipulations

***app/javascripts/channels/rooms.coffee***
```
[...]
App.global_chat = App.cable.subscriptions.create {
    channel: "ChatRoomsChannel"
    chat_room_id: messages.data('chat-room-id')
  },
  connected: ->
    # Called when the subscription is ready for use on the server

  disconnected: ->
    # Called when the subscription has been terminated by the server

  received: (data) ->
    messages.append data['message']

  send_message: (message, chat_room_id) ->
    @perform 'send_message', message: message, chat_room_id: chat_room_id
[...]
```

The only thing...

***app/javascripts/channels/rooms.coffee***
```
jQuery(document).on 'turbolinks:load', ->
  messages = $('#messages')
  if $('#messages').length > 0
    messages_to_bottom = -> messages.scrollTop(messages.prop("scrollHeight"))

    messages_to_bottom()

    App.global_chat = App.cable.subscriptions.create
    # ...
```

Let’s also scroll ...

***app/javascripts/channels/rooms.coffee***
```
[...]
received: (data) ->
  messages.append data['message']
  messages_to_bottom()
[...]
```
