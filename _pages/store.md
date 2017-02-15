---
layout: inner
title: Tienda
lead_text: Tutorial Tienda Virtual
permalink: /tienda/
---

### Repostitorio de la aplicación
[https://github.com/railsgirls-cali/example-store-2017](https://github.com/railsgirls-cali/example-store-2017)

### Demo
[https://railsgirls-cali-store-2017.herokuapp.com/](https://railsgirls-cali-store-2017.herokuapp.com/)


### Guía detalla

Puedes ver la guía más detallada en Google Docs [aquí](https://docs.google.com/document/d/1Uvk-ile_XPTGowkneNc49l2SPNSzUe7KSFKlMUrGp28/edit?usp=sharing).

## 1. Creando una aplicación nueva

En la terminal:

```
rails new tienda
```
```
cd tienda
```
```
bundle install
```

### Arranca el servidor de Rails

En la terminal:

```
rails server
```

## 2. Página de inicio

En el navegador, ve a la URL: [localhost:3000](localhost:3000) . Esta es la página de inicio por defecto para las aplicaciones Rails.

## 3. Creando el "esqueleto" para producto (generador scaffold)

Como necesitamos una tienda, pues quisiéramos tener algo para vender en ella, lo cual vamos a llamar "productos" o "products" en inglés.

Usaremos  la funcionalidad **scaffold** de Rails para generar un código base que nos permita listar, añadir, eliminar, editar y ver objetos, en nuestro caso productos.

En la terminal:

```
rails generate scaffold product name:string description:text picture:string price:float quantity:integer
```

Al correr el generador, vemos que rails de nuevo ha generado otro montón de archivos, todos ellos relacionados con lo que le llamamos productos (products).

El código que hemos generado ha debido de crear una página básica dedicada a gestionar productos (products). 

### Migraciones

Si vamos a [localhost:3000/products](localhost:3000/products) vamos a tener nuestro primer error :(

Para solucionarlo, en la terminal:
```
rake db:migrate
```

Este comando nos permite crear la tabla de productos en la base de datos dónde vamos a almacenar toda la información de la tienda.

### Validaciones
Para asegurarnos que todos nuestros productos tengan un foto vamos a agregar una validación al "Product":

```ruby
class Product < ApplicationRecord
  validates_presence_of :picture
end
```

### 4. Afinando las routes

Cómo mencionamos en el paso 2, Rails crea una página de inicio por defecto. Cambiemos nuestra página de inicio para que sea el listado de productos de nuestra tienda:

```ruby
root :to => 'products#index'
```

### 5. Mostrando la foto de nuestro producto
Por defecto en vez de la foto se está mostrando la URL. Modifiquemos la lista de productos y el detalle:

Lista de prodcutos: `app/views/products/index.html.erb`

```rhtml
<p id="notice"><%= notice %></p>

<h1>Listado de Productos</h1>

<ul>
  <% @products.each do |product| %>
    <li>
      <h3><%= product.name %></h3>
      <%= link_to image_tag(product.picture, width: '200'), product %>
      <%= number_to_currency product.price, precision: 0 %>
      <%= link_to 'Detalle', product %></li>
  <% end %>
</ul>
<p>
  <%= link_to 'New Product', new_product_path %>
</p>
```

Detalle del producto: `app/views/products/show.html.erb`

```rhtml
<p id="notice"><%= notice %></p>

<h1><%= @product.name %></h1>
<%= link_to image_tag(@product.picture, width: 300), @product %>
<p>
  <%= @product.description %>
</p>

<p>
  <strong>Precio:</strong>
  <%= number_to_currency @product.price, precision: 0 %>
</p>

<p>
  <strong>Cantidades disponibles:</strong>
  <%= @product.quantity %>
</p>

<%= link_to 'Regresar a productos', products_path %>
<%= link_to 'Eliminar producto', product_path(@product), method: :delete %>
```

## 6. Comprando un producto

Para comprar un producto vamos a tener que "tocar" todo el MVC y las rutas.

Agregamos al archivo `config/routes.rb` una nueva ruta:
```ruby
get 'products/:id/purchase', to: 'products#purchase', as: :purchase_product
```

Lo siguiente es modificar el controlador `app/controllers/products_controller.rb` agregando la acción comprar (purchase):
```ruby
def purchase
  @product = Product.find(params[:id])
  @product.decrement_quantity
  @product.save!

  respond_to do |format|
    format.html { redirect_to @product, notice: 'Producto comprado' }
  end
end
```

Añadimos al modelo `app/models/product.rb` un nuevo método:
```ruby
def decrement_quantity
  self.quantity -= 1
end
```

Por último en `app/views/products/show.html.erb`, agregamos un botón después del precio:
```rhtml
<h3>
  <% if @product.quantity > 0 %>
    <%= link_to 'Comprar', purchase_product_path(@product), style: "color:blue" %>
  <% else %>
    <%= link_to 'Lo lamentamos, se han acabado las unidades disponibles', products_path, style: "color:blue" %>
  <% end %>
</h3>
```

Prueba haciendo click en un producto para ver el detalle y presionando el botón comprar para ver como se decrementan las unidades disponibles.


## 7. Embellecimiento
La aplicación no luce muy bien todavía. Vamos a hacer algo con esto. Usaremos el proyecto Bootstrap para darle estilo en forma fácil.

### Estilos

Agregamos una nueva **gema** (libreria) `config/Gemfile`:

```ruby
gem 'bootstrap-sass', '~> 3.3.6'
```

Cambiamos la **extensión** del archivo `app/assets/stylesheets/application.css` por `scss` y reemplazmos su contenido por:
```scss
@import "bootstrap-sprockets";
@import "bootstrap";

@import "products";
@import "scaffolds";
```
**Nota:** Debemos reiniciar el servidor después de hacer este cambio.

Ahora agregamos los estilos.

Agregamos al archivo `app/assets/stylesheets/application.scss`:

```scss
.navbar-default {
  background-color: #d3360b;
  a {
    color: white !important;
  }
  .navbar-brand {
    font-size: 24px;
  }
}
```

Sustituimos completamente el archivo `app/assets/stylesheets/products.scss`:
```scss
.product-cont {
  text-align: center;
  h3 a {
    color: #d3360b;
    margin-bottom: 12px;
  }
  a:hover {
    background: none;
  }
  p {
    margin-top: 10px;
    font-size: 16px;
  }
}

.product-details {
  h1 {
    color: #d3360b;
    margin-bottom: 24px;
  }
  p {
    font-size: 18px;
  }
  .description {
    margin-top: 100px;
  }
}
```

Sustituimos completamente el archivo `app/assets/stylesheets/scaffolds.scss`:

```scss

body {
  background-color: #fff;
  color: #333;
  font-family: verdana, arial, helvetica, sans-serif;
  font-size: 13px;
  line-height: 18px;
}

p, ol, ul, td {
  font-family: verdana, arial, helvetica, sans-serif;
  font-size: 13px;
  line-height: 18px;
}

pre {
  background-color: #eee;
  padding: 10px;
  font-size: 11px;
}

a {
  color: #000;

  &:visited {
    color: #666;
  }

  &:hover {
    color: #fff;
    background-color: #000;
  }
}

div {
  &.field, &.actions {
    margin-bottom: 10px;
  }
}

#notice {
  color: green;
}

.field_with_errors {
  padding: 2px;
  background-color: red;
  display: table;
}

#error_explanation {
  width: 450px;
  border: 2px solid red;
  padding: 7px;
  padding-bottom: 0;
  margin-bottom: 20px;
  background-color: #f0f0f0;

  h2 {
    text-align: left;
    font-weight: bold;
    padding: 5px 5px 5px 15px;
    font-size: 12px;
    margin: -7px;
    margin-bottom: 0px;
    background-color: #c00;
    color: #fff;
  }

  ul li {
    font-size: 12px;
    list-style: square;
  }
}
```
### Vistas

También tenemos que actualizar las vistas para aplicar estos estilos. 

Primero actualizamos el "encuadre" de la aplicación. Sustituimos completamente el archivo `app/views/layouts/application.html.erb`:

```rhtml
<!DOCTYPE html>
<html>
<head>
  <title>Tienda Rails Girls Cali 2017</title>
  <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track' => true %>
  <%= javascript_include_tag 'application', 'data-turbolinks-track' => true %>
  <%= csrf_meta_tags %>
</head>
<body>
  <%= render 'layouts/header' %>
  <% if notice.present? %>
    <div id="notice" class="alert alert-success alert-dismissible">
      <%= notice %>
    </div>
  <% end %>
  <div class="container-fluid">
    <%= yield %>
  </div>
</body>
</html>
```

Como se pueden dar cuenta en el **layout** de la aplicación, estamos **renderizando** un archivo `header` (la cabecera). El contendio de este archivo será incluido en el layout.

Entonces creamos un nuevo archivo `app/views/layouts/_header.html.erb`, con el siguiente contenido:
```rhtml
<nav class="navbar navbar-default">
  <div class="container-fluid">
    <!-- Brand and toggle get grouped for better mobile display -->
    <div class="navbar-header">
      <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false">
        <span class="sr-only">Toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <%= link_to 'Tienda Rails Girls Cali', root_path, class: "navbar-brand" %>
    </div>
  </div>
</nav>
```

Además del layout debemos actualizar las demás vistas de productos. 
Para esto vamos a reemplazar todo el código de `app/views/products/index.html.erb`, `show.html.erb`, `new.html.erb`, `edit.html.erb` y `form.html.erb`.

Vamos al [repositorio](https://github.com/railsgirls-cali/example-store-2017) para copiar el código de estas vistas.

## 8. Buscando Productos

Para hacer la aplicación más interesante y útil, sería ideal poder buscar por los productos de manera fácil y rápida desde cualquier página.

Para ello, vamos a colocarle un campo de búsqueda en la cabecera (header) que acabamos de poner.

```rhtml
<%= form_tag search_products_path, class: 'navbar-form navbar-left pull-right',
             role: 'search', method: :get do %>
  <div class="form-group">
    <%= text_field_tag :product_name, @product_name, class: 'form-control',
                       placeholder: 'Buscar productos' %>
  </div>
  <%= submit_tag 'Buscar', class: 'btn btn-default' %>
<% end %>
```
Ahora agregamos una nueva ruta para las búsquedas, en el archivo `config/routes.rb` modificamos:

`resources :products`

por

```ruby
resources :products do
  get 'search', on: :collection
end
``` 

Esto hará que nuestra aplicación responda a la url `/products/search` (que es lo mismo que el search_products_path que se ve en el código agregado) que es a donde nuestro formulario enviará los datos ingresados en el campo de texto de búsqueda.

Agregamos la nueva acción  **"buscar"** al controlador `app/controllers/products_controller.rb`:
```ruby
def search
  @product_name = params[:product_name]
  @products = Product.search(@product_name)
end
```

También debemos ir a nuestro modelo de Producto (que se comunica con la base de datos) `app/models/product.rb`  y agregar la lógica de búsqueda como tal:

```ruby
def self.search(term)
  self.where("lower(name) LIKE lower(?)", "%#{term}%")
end
```

Lo que hemos escrito significa que va a buscar los productos por nombre, sin importar mayúsculas o minúsculas.

Por último creamos la vista `app/views/products/search.html.erb` y colocamos lo siguiente:
```rhtml
<h1><%= "Resultados de productos: #{@product_name}" %></h1>
<br>
<br>
<ul>
  <% @products.each do |product| %>
    <li>
      <h3><%= product.name %></h3>
      <%= link_to image_tag(product.picture, width: '200'), product %>
      <%= number_to_currency product.price, precision: 0 %>
      <%= link_to 'Detalle', product %></li>
  <% end %>
</ul>

<%= link_to 'Regresar a productos', products_path %>
```
Refresca la página y escribe una palabra o parte de ella en la caja de búsqueda para ver los resultados de productos.
 
 
## 9. ¿Quién administra mi tienda?

En esta parte vamos a realizar las funcionalidades de crear, editar y eliminar productos. Esto lo vamos a hacer en una ruta diferente a la que acceden los usuarios normales, que es la ruta del administrador.

Primero vamos a crear las siguientes carpetas `app/controllers/admin` , `app/views/admin` y `app/views/admin/products`.

Dentro de `config/routes.rb` agregamos:
```ruby
namespace :admin do
  resources :products
end
```

Una vez tenemos la ruta vamos a crear el controlador `app/controllers/admin/products_controller.rb`:

```ruby
class Admin::ProductsController < ApplicationController

  def index
    @products = Product.all

    respond_to do |format|
      format.html # index.html.erb
      format.json { render json: @products }
    end
  end

  def new
    @product = Product.new

    respond_to do |format|
      format.html # new.html.erb
      format.json { render json: @product }
    end
  end

  def edit
    @product = Product.find(params[:id])
  end

  def create
    @product = Product.new(product_params)

    respond_to do |format|
      if @product.save
        format.html { redirect_to admin_products_url, notice: 'Producto creado.' }
        format.json { render json: @product, status: :created, location: @product }
      else
        format.html { render action: "new" }
        format.json { render json: @product.errors, status: :unprocessable_entity }
      end
    end
  end

  def update
    @product = Product.find(params[:id])

    respond_to do |format|
      if @product.update_attributes(product_params)
        format.html { redirect_to admin_products_url, notice: 'Producto actuaizado.' }
        format.json { head :no_content }
      else
        format.html { render action: "edit" }
        format.json { render json: @product.errors, status: :unprocessable_entity }
      end
    end
  end

  def destroy
    @product = Product.find(params[:id])
    @product.destroy

    respond_to do |format|
      format.html { redirect_to admin_products_url, notice: 'Producto eliminado.'}
      format.json { head :no_content }
    end
  end

  private
  # Never trust parameters from the scary internet, only allow the white list through.
  def product_params
    params.require(:product).permit(:name, :description, :picture, :price, :quantity)
  end
end
```

El siguiente y último paso es actulizar las vistas.

Eliminámos los archivos `app/views/products/_form.html.erb`, `app/views/products/edit.html.erb` y `app/views/products/new.html.erb`.

Creamos el archivo `app/views/admin/products/_form.html.erb`:
```rhtml
<%= form_for [:admin, @product] do |f| %>
  <% if @product.errors.any? %>
    <div id="error_explanation">
      <h2><%= pluralize(@product.errors.count, "error") %> prohibited this product from being saved:</h2>

      <ul>
      <% @product.errors.full_messages.each do |message| %>
        <li><%= message %></li>
      <% end %>
      </ul>
    </div>
  <% end %>

  <div class="field">
    <label>Nombre:</label><br>
    <%= f.text_field :name %>
  </div>
  <div class="field">
    <label>Descripción:</label><br>
    <%= f.text_area :description %>
  </div>
  <div class="field">
    <label>Imágen:</label><br>
    <%= f.text_field :picture %>
  </div>
  <div class="field">
    <label>Precio:</label><br>
    <%= f.text_field :price %>
  </div>
  <div class="field">
    <label>Cantidad:</label><br>
    <%= f.number_field :quantity %>
  </div>
  <div class="actions">
    <%= f.submit 'Guardar' %>
  </div>
<% end %>
```

Creamos el archivo `app/views/admin/products/edit.html.erb`:

```rhtml
<h1>Editar Producto</h1>

<%= render 'form' %>

<%= link_to 'Regresar', admin_products_path %>
```

Creamos el archivo `app/views/admin/products/new.html.erb` y colocamos en el:
```rhtml
<h1>Crear Producto</h1>

<%= render 'form' %>

<%= link_to 'Regresar', admin_products_path %>
```

Creamos el archivo `app/views/admin/products/index.html.erb`:
```rhtml
<p id="notice"><%= notice %></p>

<h1>Listado de Productos</h1>

<table>
  <thead>
    <tr>
      <th>Picture</th>
      <th>Nombre</th>
      <th>Descripción</th>
      <th>Precio</th>
      <th>Cantidad</th>
      <th colspan="3"></th>
    </tr>
  </thead>

  <tbody>
    <% @products.each do |product| %>
      <tr>
        <td><%= image_tag product.picture, width: '50' %></td>
        <td><%= product.name %></td>
        <td><%= product.description %></td>
        <td><%= number_to_currency product.price, precision: 0 %></td>
        <td><%= product.quantity %></td>
        <td><%= link_to 'Editar', edit_admin_product_path(product) %></td>
        <td><%= link_to 'Borrar', admin_product_path(product), method: :delete,
                        data: { confirm: 'Estás seguro que deseas borrar este producto?' } %></td>
      </tr>
    <% end %>
  </tbody>
</table>
<br>
<%= link_to 'Nuevo Producto', new_admin_product_path %>
```

Ahora podemos ir a nuestro navegador web, usando la ruta `/admin/products`, por ejemplo, para ver una lista de productos pero poder administrarlos, la idea de hacer esto es para que haya una parte de la aplicación encargada de la administración y otra separada para hacer las compras, posibilitando que luego podamos añadir más fácilmente permisos de acceso.

## 10. Registrando usuarios (autenticación)

Vamos a agregar una simple gema de autenticación llamada Devise. Esta nos proporciona formularios de autenticación y métodos para manejar las sesiones de usuario.

Lo primero que tenemos que hacer es instalar la gema. Agregamos al archivo `Gemfile` la línea:
```ruby
gem 'devise'
```

**Info**: [https://github.com/plataformatec/devise](https://github.com/plataformatec/devise)

Ahora instalamos la gema mediante el comando en la terminal:
```
bundle install
```

Configuramos nuestro proyecto para usar Devise con:
```
rails generate devise:install
```

Creamos un modelo de Devise para el administrador:
```
rails generate devise Admin
```

Ahora necesitamos crear un usuario administrador en nuestra base de datos, para esto abrimos la consola de Rails escribiendo:
```
rake db:migrate
```

Creamos un usuario administrador directamente en la consola de Rails:
```
Admin.create(email: 'admin@tienda.com', password: 'railsgirls', password_confirmation: 'railsgirls')
```

Y en el controlador de productos para administradores (`app/controllers/admin/products_controller.rb`) le decimos que antes de hacer cualquier acción debe autenticar el administrador:
```ruby
before_action :authenticate_admin!
```

Reiniciamos el servidor de Rails y vamos a la dirección `http://localhost:3000/admin/products`. Ahora nos debería pedir autenticarnos. Lo hacemos con los datos de email y password del usuario administrador creado anteriormente.

Modificamos la barra de navegación del layout principal `app/views/layouts/header.html` como lo hicimos en una anterior ocasión, para agregar un enlace para cerrar la sesión:
```rhtml
<% if admin_signed_in? %>
  <ul class="nav navbar-nav navbar-right">
    <li>
      <%= link_to "Cerrar Sesión", destroy_admin_session_path, method: :delete %>
    </li>
  </ul>
<% end %>
```

Refrescamos la página y probamos el enlace de cierre de sesión.

Eso es todo por ahora, esperamos que tu tienda esté funcionando y que tengas las bases para seguir avanzando. ;)

# Bonus track

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
9. Crea un repositorio nuevo vacío para tu nuevo proyecto. Desde tu repositorio, copia el enlace SSH:
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
```
```
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
heroku run rake db:migrate #Para correr las migraciones
```