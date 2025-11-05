---
layout: inner
title: Guía 2025 - Tienda
lead_text: ¡Crea tu primera tienda online en Rails!
permalink: /guia/
---

¡Tu Primera Aventura con Rails!
==========================

¡Hola y bienvenida! 👋 Esta guía te va a enseñar cómo crear tu primera aplicación web con Ruby on Rails. ¡Sí, vas a construir una aplicación web de verdad!

Después de completar esta guía, sabrás:

* ✨ Cómo crear tu propia aplicación Rails desde cero
* 🏗️ Cómo están organizadas las aplicaciones web (su "arquitectura")
* 🎨 Cómo crear páginas que las personas puedan visitar en internet
* 💾 Cómo guardar y recuperar información (como productos en una tienda)
* 🎯 Los conceptos básicos que usan los programadores profesionales todos los días

--------------------------------------------------------------------------------

Introducción: ¿Qué Vamos a Hacer?
------------

¡Prepárate para algo emocionante! Vas a aprender a construir aplicaciones web con Ruby on Rails. ¿Qué significa eso?

Imagina que quieres construir una casa. Podrías hacer todo desde cero: cortar los árboles para hacer la madera, fabricar los clavos, crear el cemento... ¡Tomaría años! En lugar de eso, usas un kit de construcción con materiales listos, instrucciones claras y herramientas que facilitan el trabajo.

**Rails es exactamente eso, pero para construir sitios web.** Es un kit de herramientas que te da todo lo necesario para crear aplicaciones web increíbles, sin tener que inventar todo desde cero.

💡 **Algo importante:** Rails está construido con un lenguaje de programación llamado Ruby. Es como aprender a usar una varita mágica: necesitas conocer algunos hechizos básicos (Ruby) para poder hacer la magia (Rails). No te preocupes, iremos aprendiendo Ruby poco a poco mientras avanzamos.

Si quieres practicar Ruby antes (¡es divertido!), aquí hay algunos recursos:

- [¿Tienes 30 minutos? ¡Prueba Ruby ahora mismo!](https://try.ruby-lang.org/)
- [Sitio web oficial del lenguaje de programación Ruby](https://www.ruby-lang.org/en/documentation/)
- [Lista de libros gratuitos de programación](https://github.com/EbookFoundation/free-programming-books/blob/main/books/free-programming-books-langs.md#ruby)

La Filosofía de Rails: ¿Por Qué Es Tan Especial?
----------------

¿Alguna vez has usado una receta de cocina? Una buena receta te dice exactamente qué ingredientes necesitas, en qué orden mezclarlos, y cuánto tiempo cocinar. No tienes que inventar todo desde cero. Rails funciona igual: te da las "recetas" para construir aplicaciones web de forma fácil y rápida.

Rails fue creado con una idea en mente: **hacer que programar sea más divertido y menos repetitivo.** Los programadores que usan Rails dicen que les permite escribir menos código pero crear más cosas increíbles. ¡Es como tener superpoderes!

Rails tiene "opiniones" sobre cómo hacer las cosas. Es como cuando tu maestra te enseña la mejor forma de resolver un problema de matemáticas. Podrías hacerlo de otra manera, pero si sigues el método que te enseñan, ¡todo es más fácil!

### Los Dos Principios Mágicos de Rails ✨

Rails se basa en dos ideas súper importantes. Piensa en ellas como las reglas de un juego que hacen todo más divertido:

#### 1. **No Te Repitas (Don't Repeat Yourself - DRY)**

Imagina que estás escribiendo una historia y tienes que describir a tu personaje principal. ¿Escribirías su descripción completa cada vez que aparece en la historia? ¡Claro que no! Lo haces una vez al principio.

En programación es igual. Si necesitas usar la misma información en varios lugares, la escribes **una sola vez** y luego la reutilizas. Esto hace que tu código sea:
- 🎯 Más fácil de leer
- 🔧 Más fácil de cambiar (solo cambias en un lugar, no en 100)
- 🐛 Con menos errores (menos lugares donde equivocarte)

#### 2. **Convención Sobre Configuración (Convention Over Configuration)**

¿Sabes cuando entras a un supermercado nuevo? Todos los supermercados están organizados de forma similar: la leche en el área de refrigerados, el pan en la panadería, las frutas juntas. No tienes que buscar por todo el lugar.

Rails hace lo mismo. Tiene reglas sobre dónde poner cada cosa en tu aplicación. Si sigues estas reglas:
- ✅ No tienes que tomar mil decisiones pequeñas
- ✅ Otros programadores entienden tu código fácilmente
- ✅ Rails hace mucho del trabajo automáticamente

Es como tener un ayudante invisible que sabe exactamente dónde va cada cosa. ¡Súper útil!

¡Vamos a Construir Nuestra Primera Aplicación!
------------------------

¡Aquí viene lo emocionante! Vas a crear tu propia tienda en línea (una "store" en inglés). ¡Sí, una tienda de verdad donde podrías vender productos! 🛍️

Nuestra tienda va a tener:
- 📦 Productos que puedes mostrar
- 📝 Formularios para agregar nuevos productos
- 🔐 Un sistema para que solo personas autorizadas puedan agregar o editar productos

💡 **Consejo útil:** A lo largo de esta guía verás comandos que empiezan con el símbolo `$`. Ese símbolo NO lo escribes tú - solo te indica que es un comando para la terminal (la ventanita oscura donde escribes instrucciones a la computadora).

### ¿Qué Necesitas Para Empezar?

Antes de comenzar nuestra aventura, necesitas tener listo lo siguiente:

* 💻 **Una cuenta de GitHub** - Es como tu perfil de red social, pero para guardar código
* 🌟 **Ruby 3.2 o más reciente** - El lenguaje de programación (no te preocupes, ya estará instalado)
* 🚀 **Rails 8.1.0 o más reciente** - Nuestro kit de herramientas mágico (también ya estará instalado)
* ✍️ **Un editor de código** - Donde escribirás tu código (ya estará listo en Codespaces)

### Creando Tu Taller de Trabajo en la Nube 🛠️

Imagina que vas a hornear galletas. Necesitas un lugar con un horno, ingredientes, utensilios, y una mesa limpia para trabajar. Un **ambiente de desarrollo** es exactamente eso, ¡pero para programar!

Es el espacio donde:
- ✍️ Escribes tu código
- 🧪 Pruebas que todo funcione
- 🔧 Arreglas errores
- 🎨 Ves cómo se ve tu aplicación antes de que otras personas la usen

Para este proyecto, vamos a usar algo súper cool llamado **GitHub Codespaces**. Es como tener un taller completo de programación en internet. Imagina que abres tu navegador y ¡PUM! Ya tienes todo listo: el editor donde escribirás código, la terminal para dar comandos, ¡y todo funciona sin tener que instalar nada en tu computadora!

#### Paso 1: Asegúrate de Tener Tu Cuenta de GitHub

Antes que nada, necesitas una cuenta de GitHub. Es como crear una cuenta en cualquier red social, pero esta es especial para programadores. GitHub guarda tu código y te permite trabajar en proyectos desde cualquier lugar.

¿No tienes cuenta todavía? No te preocupes, es gratis y fácil. Sigue esta [guía para crear tu cuenta](https://docs.github.com/es/get-started/start-your-journey/creating-an-account-on-github).

#### Paso 2: Crea Tu Propia Copia del Proyecto

¡Ahora viene la parte divertida! Vamos a usar una "plantilla" que ya tiene todo preparado para ti. Es como cuando en arte te dan un dibujo con el contorno y tú lo coloreas y agregas detalles.

Sigue estos pasos (¡es más fácil de lo que parece!):

1. **Abre la plantilla:** Ve a [store-template](https://github.com/railsgirls-cali/store-template)

2. **Crea tu copia:** Busca el botón verde que dice "Use this template" (Usar esta plantilla). Haz clic ahí y selecciona "Create a new repository" (Crear un nuevo repositorio).

3. **Dale un nombre:** Ponle un nombre a tu proyecto. Puedes usar `store` o `mi-tienda` o lo que quieras. Luego haz clic en "Create repository" (Crear repositorio).

4. **Abre tu taller en la nube:** En tu nuevo repositorio, busca el botón verde "Code" (Código). Haz clic ahí y verás una pestaña que dice "Codespaces". ¡Haz clic en esa pestaña!

5. **Crea tu Codespace:** Ahora haz clic en "Create codespace on main" (Crear codespace en main).

¡Listo! GitHub empezará a preparar tu taller de trabajo. Verás muchas cosas cargando - eso es normal. Es como cuando instalas un videojuego y tiene que descargar un montón de archivos. Puede tomar unos minutos la primera vez, así que ten paciencia. ☕

✨ **Dato curioso:** Si algún día quieres instalar Rails en tu propia computadora, puedes consultar la [Guía de Instalación de Ruby on Rails](https://guides.rubyonrails.org/install_ruby_on_rails.html). ¡Pero hoy no necesitas hacer eso!

#### Paso 3: ¡Verifica Que Todo Esté Listo!

Una vez que tu Codespace esté listo (verás un editor de código con varios archivos y carpetas), vamos a asegurarnos de que Rails esté instalado correctamente.

¿Ves la parte de abajo donde hay una ventana negra o azul oscura? Esa es la **terminal** - tu línea directa para darle órdenes a la computadora. ¡Es como una varita mágica!

Escribe esto en la terminal (recuerda: NO escribas el símbolo $, solo lo que viene después):

```bash
$ rails --version
Rails 8.1.0
```

Presiona Enter. Si todo está bien, verás un número de versión como `Rails 8.1.0` o superior. ¡Eso significa que Rails está listo para la acción! 🎉

🤔 **¿Ves un número diferente?** No te preocupes. Mientras sea 8.1.0 o un número más alto, ¡estás lista para continuar!

### ¿Cómo se Crea Normalmente una Aplicación Rails?

Rails es como tu asistente personal. Tiene muchos "comandos mágicos" que hacen cosas increíbles por ti. Si alguna vez quieres ver todos estos comandos, puedes escribir `rails --help` en la terminal.

💡 **Algo que debes saber:** Normalmente, cuando los programadores quieren crear una aplicación Rails nueva desde cero, usan un comando especial llamado `rails new`. Este comando es como un constructor robot que crea todo lo que necesitas en segundos.

Si estuvieras empezando desde cero (pero hoy no lo haremos), escribirías:

```bash
$ rails new store
```

¡BOOM! 💥 Este comando crearía:
- 📁 Todas las carpetas organizadas perfectamente
- ⚙️ Archivos de configuración listos para usar
- 🔧 Herramientas predeterminadas instaladas
- 📄 Archivos iniciales para empezar a programar

Es como ordenar una casa prefabricada que llega lista con los cuartos, puertas, y ventanas ya instaladas.

Después, entrarías a tu nueva aplicación con:

```bash
$ cd store
```

(El comando `cd` significa "change directory" - cambiar de carpeta. Es como entrar a un cuarto diferente en tu casa.)

✨ **Pero adivina qué:** ¡Ya tienes todo esto listo en tu Codespace! Alguien ya hizo la parte aburrida por ti. Así que puedes saltar directo a la parte divertida: ¡programar!

### Tu Nueva Casa: Explorando las Carpetas 🏠

¡Mira todas esas carpetas y archivos en tu editor! Puede parecer mucho al principio, pero no te preocupes. Piensa en tu aplicación Rails como una casa nueva. Cada cuarto tiene un propósito específico:

- La cocina es para cocinar 🍳
- El cuarto es para dormir 🛏️
- El baño es para... bueno, ya sabes 🚿

En Rails, cada carpeta también tiene un trabajo específico. Vamos a conocer las más importantes (¡no tienes que memorizar todo ahora!):

#### 📂 Las Carpetas Súper Importantes (donde pasarás la mayoría del tiempo):

**🎨 app/** - ¡Esta es TU carpeta estrella!
Aquí es donde pasarás el 90% de tu tiempo. Contiene todo el código que hace funcionar tu aplicación:
- Los **models** (cómo guardas información)
- Los **views** (lo que ven las personas en el navegador)
- Los **controllers** (el cerebro que decide qué hacer)

**⚙️ config/** - El cuarto de control
Aquí es donde le dices a Rails cómo debe comportarse tu aplicación. Por ejemplo:
- Qué rutas (URLs) existen en tu aplicación
- Cómo conectarse a la base de datos
- Configuraciones especiales

**💾 db/** - Tu biblioteca de información
Aquí vive tu base de datos (donde guardas todos los productos, usuarios, etc.) y las instrucciones para crearla y modificarla.

#### 📂 Otras Carpetas Útiles (las conocerás después):

**📄 public/** - Archivos que todos pueden ver
Como el buzón de tu casa - cualquier persona puede ver lo que está aquí sin necesitar permisos especiales. Imágenes, archivos CSS, etc.

**📝 log/** - El diario de tu aplicación
Aquí Rails escribe un registro de todo lo que pasa. Si algo sale mal, puedes leer estos archivos para descubrir qué pasó. ¡Como un detective! 🔍

**🧪 test/** - Tu laboratorio de experimentos
Donde escribes código para asegurarte de que todo funciona correctamente.

💡 **Consejo de pro:** No te agobies con todas estas carpetas ahora. Por ahora, solo necesitas saber que existe la carpeta **app/** - ahí es donde crearás la magia. Las demás carpetas son como los cuartos de servicio de una casa: están ahí y son importantes, pero no necesitas entrar todo el tiempo.

### El Secreto de Rails: Model-View-Controller (MVC) 🎭

¿Recuerdas cuando fuiste a un restaurante? Hay diferentes personas haciendo diferentes trabajos:
- 📋 El **mesero** toma tu orden y te trae la comida
- 👨‍🍳 El **chef** cocina tu comida en la cocina
- 🍽️ El **plato bonito** en el que presentan tu comida

Rails funciona exactamente igual, pero con código. Se llama **MVC** (Model-View-Controller), y son las tres partes que trabajan juntas para hacer funcionar tu aplicación:

#### 🎨 **View (Vista)** - El Escaparate Bonito

La **View** es lo que las personas VEN en su navegador. Es como el escaparate decorado de una tienda o el menú bonito de un restaurante.

Ejemplos:
- La página que muestra todos los productos
- Un formulario donde agregas un producto nuevo
- La página de inicio de tu tienda

Es puro diseño y presentación. HTML, colores, texto visible. ¡La parte bonita!

#### 🧠 **Controller (Controlador)** - El Cerebro que Decide

El **Controller** es como el mesero del restaurante. Cuando alguien hace una petición (como visitar una página), el controller:
1. Recibe la petición ("Quiero ver todos los productos")
2. Decide qué hacer
3. Pide la información necesaria al Model
4. Le dice al View qué mostrar

Es el que coordina todo. ¡El director de orquesta! 🎼

#### 💾 **Model (Modelo)** - El Guardián de la Información

El **Model** es como la base de datos de fichas de una biblioteca. Aquí es donde:
- Se guarda toda tu información (productos, usuarios, etc.)
- Se definen las reglas (un producto DEBE tener nombre)
- Se organizan los datos

Es el que sabe TODO sobre tu información y cómo manejarla.

#### ¿Cómo Trabajan Juntos? 🤝

Imagina que alguien visita tu tienda en línea:

1. **Persona:** "Quiero ver los productos" (hace clic en un enlace)
2. **Controller:** "¡OK! Mesero al rescate. Voy a pedirle al Model todos los productos"
3. **Model:** "Aquí están los 10 productos de la base de datos"
4. **Controller:** "Perfecto. View, muéstralos de forma bonita"
5. **View:** "¡Aquí está! Una página hermosa con los 10 productos"
6. **Persona:** "¡Wow, qué bonito!"

<picture class="flowdiagram">
  <source srcset="/assets/images/guides/mvc_architecture_dark.jpg" media="(prefers-color-scheme:dark)">
  <img src="/assets/images/guides/mvc_architecture_light.jpg">
</picture>

💡 **¿Por qué es genial separar todo así?** Porque cada parte tiene un trabajo específico. Es como en un equipo deportivo: cada persona tiene su posición y todos trabajan juntos. Si necesitas cambiar cómo SE VE algo, solo cambias el View. Si necesitas cambiar cómo se GUARDA la información, solo cambias el Model. ¡Súper organizado!

¡Ya casi lo tienes! Ahora vamos a ver todo esto en acción.

¡Momento Mágico: Tu Primera Aplicación Web! ✨
-------------

¡Este es el momento que has estado esperando! Vas a arrancar tu aplicación web por primera vez. ¿Lista? ¡Vamos!

### Paso 1: Preparar la Base de Datos

Normalmente, antes de iniciar una aplicación Rails, necesitarías crear la base de datos con este comando:

```bash
$ bin/rails db:create
```

Este comando le dice a Rails: "¡Crea mi base de datos!" Es como preparar una carpeta nueva y vacía para guardar fichas.

✨ **¡Buenas noticias!** En tu Codespace, alguien ya hizo esto por ti. La base de datos ya está lista y esperando. Así que podemos saltar directamente a la parte emocionante.

### Paso 2: ¡Enciende el Motor! 🚀

Ahora viene lo increíble. Vas a iniciar tu **servidor web**. ¿Qué es un servidor? Imagina una cocina que está siempre lista para preparar comida cuando alguien hace un pedido. El servidor de Rails está siempre escuchando, esperando que alguien visite tu aplicación.

En tu terminal, escribe este comando mágico:

```bash
$ bin/rails server
```

💡 **¿Por qué `bin/rails`?** Cuando escribes `bin/rails` en lugar de solo `rails`, le estás diciendo a la computadora: "Usa la versión de Rails que está específicamente en ESTA aplicación". Es como decir "usa las herramientas de MI caja de herramientas, no las de cualquier otra caja."

Presiona Enter y... ¡mira lo que pasa! Verás un montón de texto. No te asustes, ¡es bueno! Algo como esto:

```bash
=> Booting Puma
=> Rails 8.1.0 application starting in development
=> Run `bin/rails server --help` for more startup options
Puma starting in single mode...
* Puma version: 6.4.3 (ruby 3.3.5-p100) ("The Eagle of Durango")
*  Min threads: 3
*  Max threads: 3
*  Environment: development
*          PID: 12345
* Listening on http://127.0.0.1:3000
* Listening on http://[::1]:3000
Use Ctrl-C to stop
```

¿Qué significa todo esto?
- **"Booting Puma"** - Puma es el nombre del servidor web. ¡Se está iniciando!
- **"Listening on..."** - Significa "Estoy escuchando y listo para recibir visitantes"
- **"Use Ctrl-C to stop"** - Si alguna vez quieres apagar el servidor, presionas Ctrl+C en tu teclado

¡Tu aplicación está VIVA! 🎉

### Paso 3: ¡Visita Tu Aplicación!

En GitHub Codespaces, pasará algo cool cuando el servidor arranque. Verás una notificación emergente que dice algo como "Tu aplicación está corriendo en el puerto 3000".

Codespaces es inteligente y abrirá automáticamente una pequeña ventana de preview dentro del editor. ¡Pero espera! Para la mejor experiencia, haz clic en el botón que dice algo como "Open in Browser" (Abrir en navegador) o busca el ícono de globo 🌐 junto al puerto 3000.

Cuando abras tu aplicación en el navegador, verás... ¡la página de bienvenida de Rails!

Es una página que dice algo como "Yay! You're on Rails!" (¡Sí! ¡Estás en Rails!). ¡Es la prueba de que TODO está funcionando perfectamente!

![Página de bienvenida de Rails](/assets/images/guides/rails_welcome.png)

**¡INCREÍBLE! ¡Lo lograste!** 🎉🎊

Esta página es como un semáforo en verde que te dice: "¡Todo está bien! Tu aplicación está lista para la acción." Es la primera de muchas páginas increíbles que vas a crear.

⚠️ **¿Quieres detener el servidor?** Si necesitas detener tu servidor Rails en cualquier momento (por ejemplo, para ejecutar otros comandos en la terminal), presiona `Ctrl-C` en tu teclado. Para volverlo a iniciar, simplemente ejecuta `bin/rails server` de nuevo.

### La Magia de Rails: Recarga Automática ✨

¿Sabes lo que es súper cool de Rails? Tiene una característica mágica que hace la programación mucho más divertida.

Imagina que estás construyendo con bloques de LEGO. ¿Qué pasaría si cada vez que quisieras agregar un bloque nuevo, tuvieras que desarmar TODA tu construcción y empezar de cero? ¡Sería súper frustrante!

Bueno, Rails NO te hace eso. Tiene algo llamado **recarga automática** (autoloading). ¿Qué significa?

🔄 **Mientras tu servidor está corriendo, puedes:**
- Crear archivos nuevos
- Cambiar archivos existentes
- Agregar código

Y Rails automáticamente detecta los cambios y los aplica. **¡No tienes que reiniciar el servidor!** Simplemente recarga la página en tu navegador y ¡voilà! Tus cambios ya están ahí.

Es como tener un ayudante invisible que dice: "¡Oh, agregaste algo nuevo! Déjame incorporarlo inmediatamente sin molestar lo demás."

💡 **Dato técnico cool:** En otros lenguajes de programación, tienes que escribir muchas líneas diciendo "usa este archivo" y "necesito este código". Rails es inteligente y sabe qué archivos necesitas automáticamente basándose en los nombres que usas. ¡Una cosa menos de qué preocuparte!

¡Creando Tu Primer Model! 💾
-------------------------

¡Ahora viene algo emocionante! Vas a crear tu primer **Model**. ¿Recuerdas del MVC? El Model es el guardián de la información.

### ¿Qué es Active Record? 🤔

Antes de empezar, déjame contarte sobre **Active Record**. Es una de las partes más mágicas de Rails.

Imagina que quieres guardar información sobre productos en tu tienda. En tu cabeza piensas: "Un producto tiene un nombre, un precio, una descripción..." Eso es fácil de entender, ¿verdad?

Pero las bases de datos hablan un lenguaje super complicado llamado SQL. Es como tener que traducir tus pensamientos a un idioma alienígena cada vez que quieras guardar algo. 😰

**¡Aquí es donde Active Record salva el día!** Es como un traductor automático. Tú escribes código en Ruby (que es fácil de leer), y Active Record lo traduce automáticamente a SQL (el lenguaje de la base de datos).

Nuestra tienda usa SQLite, que es una base de datos pequeña y perfecta para aprender. ¡Es como tener una biblioteca personal en lugar de una biblioteca gigante!

### Creando el Model "Product" 📦

Vamos a crear nuestro primer model para los productos de la tienda. En tu terminal, escribe este comando mágico:

```bash
$ bin/rails generate model Product name:string
```

Vamos a entender qué acabas de escribir:
- `generate model` - "Rails, ¡genera un model nuevo!"
- `Product` - El nombre de nuestro model (siempre en SINGULAR y con mayúscula al inicio)
- `name:string` - "Este producto tiene una propiedad llamada 'name' y es de tipo texto"

Presiona Enter y... ¡mira! Rails creó un montón de archivos por ti. Verás algo como esto:

```bash
      invoke  active_record
      create    db/migrate/20240426151900_create_products.rb
      create    app/models/product.rb
      invoke    test_unit
      create      test/models/product_test.rb
      create      test/fixtures/products.yml
```

**¡WOW! ¿Qué acaba de pasar?** 😲

Rails acaba de crear automáticamente:

1. 📝 **Una "migration"** en `db/migrate/` - Las instrucciones para crear la tabla en la base de datos
2. 🎯 **Tu model** en `app/models/product.rb` - El archivo Ruby que usarás para trabajar con productos
3. 🧪 **Archivos de prueba** - Para verificar que todo funcione bien (¡los veremos después!)

💡 **¿Notaste algo importante?** Escribimos `Product` (singular) no `Products` (plural). Esto es porque un Model representa UN solo producto. Rails es súper inteligente y automáticamente sabe que si tienes un model `Product`, la tabla en la base de datos se llamará `products` (plural). ¡Convention over Configuration en acción!

### Migrations: Las Instrucciones de Construcción 🏗️

¿Recuerdas cuando dijimos que Rails creó una "migration"? Ahora vamos a ver qué es eso y por qué es tan útil.

#### ¿Qué es una Migration?

Imagina que estás reorganizando tu cuarto. Antes de empezar, escribes una lista de instrucciones:
1. "Mueve la cama a la pared izquierda"
2. "Agrega un estante nuevo para libros"
3. "Quita el escritorio viejo"

Una **migration** es exactamente eso, ¡pero para tu base de datos! Es una lista de instrucciones que le dice a la base de datos cómo cambiar su estructura.

¿Por qué es genial? Porque:
- 📝 Tienes un registro escrito de todos los cambios
- 🔄 Puedes deshacer cambios si algo sale mal
- 👥 Otros programadores pueden aplicar los mismos cambios en sus computadoras
- 🚀 Cuando tu aplicación vaya "en vivo", puedes aplicar los cambios de forma segura

#### Veamos Tu Primera Migration 🔍

En tu editor de código (la parte izquierda de tu pantalla), busca la carpeta `db/migrate/`. Verás un archivo con un nombre largo que termina en `_create_products.rb`. ¡Ábrelo!

Verás algo como esto:

```ruby
class CreateProducts < ActiveRecord::Migration[8.1]
  def change
    create_table :products do |t|
      t.string :name

      t.timestamps
    end
  end
end
```

**¡Wow! ¿Qué es todo eso?** Vamos a descifrarlo línea por línea:

🏷️ **`class CreateProducts`**
Es el nombre de tu migration. "CreateProducts" significa "Crear Productos".

📋 **`def change`**
Aquí es donde defines QUÉ cambios quieres hacer.

🏗️ **`create_table :products do |t|`**
"Crea una tabla nueva en la base de datos llamada 'products'". ¿Notaste? El model es `Product` (singular) pero la tabla es `products` (PLURAL). Rails hace esto automáticamente porque:
- Un model representa UN producto
- Una tabla contiene MUCHOS productos

✏️ **`t.string :name`**
"Crea una columna llamada 'name' que guarda texto (strings)". Es como agregar una casilla en una ficha que dice "Nombre del producto: ___________"

⏰ **`t.timestamps`**
Este es un truco mágico que crea automáticamente DOS columnas:
- `created_at` - "¿Cuándo se creó este producto?"
- `updated_at` - "¿Cuándo se modificó por última vez?"

Rails las mantiene actualizadas automáticamente. ¡Ni siquiera tienes que pensar en ellas!

### ¡Hora de Ejecutar la Migration! 🎬

Tener las instrucciones escritas está bien, ¡pero ahora hay que HACERLAS! Es hora de decirle a la base de datos: "¡Oye, crea esa tabla de productos!"

En tu terminal, escribe:

```bash
$ bin/rails db:migrate
```

Este comando le dice a Rails: "Revisa si hay migrations nuevas y ejecútalas todas".

Presiona Enter y verás algo como esto:

```bash
== 20240426151900 CreateProducts: migrating ===================================
-- create_table(:products)
   -> 0.0030s
== 20240426151900 CreateProducts: migrated (0.0031s) ==========================
```

¿Qué significa todo esto?
- ✅ "migrating" - "¡Estoy ejecutando las instrucciones!"
- ✅ "create_table(:products)" - "¡Estoy creando la tabla de productos!"
- ✅ "migrated" - "¡Listo! Todo se hizo exitosamente"
- ⏱️ "0.0031s" - "Y solo tomó 0.003 segundos" (¡súper rápido!)

**¡Felicidades!** 🎉 Acabas de crear tu primera tabla en la base de datos. Ahora tu aplicación tiene un lugar donde guardar productos.

⚠️ **¿Cometiste un error?** ¡No hay problema! Los errores son parte del aprendizaje. Si necesitas deshacer la última migration, puedes ejecutar:

```bash
$ bin/rails db:rollback
```

Es como presionar "Ctrl+Z" para deshacer. ¡Rails tiene tu espalda!

Tu Laboratorio de Experimentos: La Consola de Rails 🧪
-------------

¡Ahora viene algo súper divertido! Vas a interactuar directamente con tu base de datos usando la **consola de Rails**. Es como tener un laboratorio donde puedes experimentar con tu código sin romper nada.

### ¿Qué es la Consola?

Imagina que tienes un videojuego y quieres probar un código secreto para ver qué hace. La consola de Rails es exactamente eso: un lugar donde puedes escribir código Ruby, presionar Enter, y ver inmediatamente qué pasa. ¡Es perfecto para experimentar!

Vamos a abrir la consola. En tu terminal, escribe:

```bash
$ bin/rails console
```

Verás algo como esto:

```irb
Loading development environment (Rails 8.1.0)
store(dev)>
```

¡Ese `store(dev)>` es tu nuevo mejor amigo! Es el "prompt" que te está diciendo: "Estoy listo, escribe algo y presiona Enter".

Vamos a probar. Escribe esto:

```irb
store(dev)> Rails.version
=> "8.1.0"
```

¿Viste eso? La consola te respondió con la versión de Rails. La flecha `=>` significa "la respuesta es...".

¡Funciona! 🎉 Ahora tienes un lugar seguro donde probar código.

La Magia del Model Product 🎩✨
--------------------------

¿Recuerdas cuando creamos el model Product? Rails creó un archivo en `app/models/product.rb`. Ábrelo en tu editor y verás algo que puede parecer extraño:

```ruby
class Product < ApplicationRecord
end
```

**¡Espera un momento!** 🤔 ¿Ves eso? ¡Está casi vacío! Solo tiene dos líneas. ¿Cómo puede funcionar un model que está vacío?

### La Magia de Active Record

Aquí es donde Rails hace algo INCREÍBLE. Aunque el archivo parece vacío, Active Record es como un mago que trabaja detrás de escena.

Cuando escribes `class Product < ApplicationRecord`, le estás diciendo a Rails: "Oye, este Product es un model especial de Active Record". Y Rails responde: "¡Perfecto! Déjame conectarme a la base de datos, ver qué columnas tiene la tabla `products`, y crear automáticamente todo el código que necesitas."

Es como tener un asistente robot que dice:
- "¿Oh, la tabla tiene una columna 'name'? ¡Listo! Ahora puedes usar `product.name`"
- "¿Tiene 'created_at'? ¡Hecho! Ahora puedes ver cuándo se creó cada producto"

**¡Todo esto sin que tengas que escribir ni una línea extra de código!** 🤯

### Veámoslo en Acción

Vamos a usar la consola para ver la magia. En tu consola de Rails, escribe:

```irb
store(dev)> Product.column_names
```

Presiona Enter y verás:

```irb
=> ["id", "name", "created_at", "updated_at"]
```

**¡Mira eso!** 🌟 Rails fue a la base de datos, leyó todas las columnas, y te las mostró. Nota que hay una columna extra que no creamos: `id`. Rails la agrega automáticamente para darle a cada producto un número único (como un número de identificación).

Esto es **DRY** (Don't Repeat Yourself) en acción. En lugar de tener que escribir código para cada columna, Rails lo descubre automáticamente. ¡Menos trabajo para ti, más tiempo para crear cosas increíbles!

### ¡Creando Tu Primer Producto! 🎨

¡Ahora viene la parte más emocionante! Vas a crear tu primer producto y guardarlo en la base de datos. Es como llenar una ficha nueva en tu biblioteca.

#### Paso 1: Crear un Producto (pero todavía no guardarlo)

En tu consola de Rails, escribe esto:

```irb
store(dev)> product = Product.new(name: "T-Shirt")
=> #<Product:0x000000012e616c30 id: nil, name: "T-Shirt", created_at: nil, updated_at: nil>
```

**¿Qué acabas de hacer?** 🤔

`Product.new(name: "T-Shirt")` es como llenar una ficha en un papel:
- Creaste un producto nuevo
- Le pusiste de nombre "T-Shirt" (camiseta)
- Pero aún NO lo guardaste en la base de datos

Mira cómo `id`, `created_at` y `updated_at` dicen `nil` (que significa "vacío" o "nada"). Eso es porque todavía no está en la base de datos.

#### Paso 2: ¡Guardarlo en la Base de Datos!

Ahora vamos a guardar ese producto. Escribe:

```irb
store(dev)> product.save
  TRANSACTION (0.1ms)  BEGIN immediate TRANSACTION /*application='Store'*/
  Product Create (0.9ms)  INSERT INTO "products" ("name", "created_at", "updated_at") VALUES ('T-Shirt', '2024-11-09 16:35:01.117836', '2024-11-09 16:35:01.117836') RETURNING "id" /*application='Store'*/
  TRANSACTION (0.9ms)  COMMIT TRANSACTION /*application='Store'*/
=> true
```

**¡BOOM!** 💥 ¿Viste todo ese texto que apareció? Eso es Rails hablando con la base de datos en su idioma secreto (SQL). Le está diciendo: "¡Guarda este producto!"

La respuesta `=> true` significa "¡Éxito! Lo guardé."

Rails tomó tu producto que estaba solo en la memoria (como en un papel) y lo guardó permanentemente en la base de datos. Además, Rails automáticamente le agregó el `id`, `created_at` y `updated_at`.

Ahora mira tu producto otra vez:

```irb
store(dev)> product
=> #<Product:0x00000001221f6260 id: 1, name: "T-Shirt", created_at: "2024-11-09 16:35:01.117836000 +0000", updated_at: "2024-11-09 16:35:01.117836000 +0000">
```

**¡Mira qué cambió!** ✨
- `id: 1` - ¡Ahora tiene un número de identificación único! Es el producto #1 en tu base de datos
- `created_at` - Rails registró exactamente cuándo se creó
- `updated_at` - Y cuándo se actualizó por última vez

Rails hizo todo esto automáticamente. ¡Tú solo tuviste que escribir `.save`!

#### El Atajo: Create

Hay una forma más rápida de hacer los pasos 1 y 2 juntos. Observa:

```irb
store(dev)> Product.create(name: "Pants")
  TRANSACTION (0.1ms)  BEGIN immediate TRANSACTION /*application='Store'*/
  Product Create (0.4ms)  INSERT INTO "products" ("name", "created_at", "updated_at") VALUES ('Pants', '2024-11-09 16:36:01.856751', '2024-11-09 16:36:01.856751') RETURNING "id" /*application='Store'*/
  TRANSACTION (0.1ms)  COMMIT TRANSACTION /*application='Store'*/
=> #<Product:0x0000000120485c80 id: 2, name: "Pants", created_at: "2024-11-09 16:36:01.856751000 +0000", updated_at: "2024-11-09 16:36:01.856751000 +0000">
```

`Product.create` hace TODO de una vez: crea el producto Y lo guarda en la base de datos. ¡Súper conveniente! Ahora tienes el producto #2 (unos pantalones) guardado.

**¡Felicidades!** 🎉 ¡Acabas de agregar 2 productos a tu base de datos! Ahora tienes una camiseta y unos pantalones en tu tienda.

### Buscando Productos en Tu Base de Datos 🔍

Ahora que tienes productos guardados, ¿cómo los encuentras? Active Record te da súper poderes para buscar información en la base de datos.

¿Quieres ver TODOS los productos en tu tienda? Usa el método `all`. Es como pedirle a la bibliotecaria: "Muéstrame todas las fichas de productos".

```irb
store(dev)> Product.all
  Product Load (0.1ms)  SELECT "products".* FROM "products" /* loading for pp */ LIMIT 11 /*application='Store'*/
=> [#<Product:0x0000000121845158 id: 1, name: "T-Shirt", created_at: "2024-11-09 16:35:01.117836000 +0000", updated_at: "2024-11-09 16:35:01.117836000 +0000">,
 #<Product:0x0000000121845018 id: 2, name: "Pants", created_at: "2024-11-09 16:36:01.856751000 +0000", updated_at: "2024-11-09 16:36:01.856751000 +0000">]
```

**¡Mira eso!** 🌟 Rails fue a la base de datos, buscó TODOS los productos, y te los mostró en una lista. Puedes ver tus dos productos: la camiseta (id: 1) y los pantalones (id: 2).

Active Record convirtió automáticamente cada fila de la base de datos en un objeto Product de Ruby. ¡Así puedes trabajar con ellos fácilmente!

💡 **Dato técnico:** `Product.all` devuelve algo llamado `ActiveRecord::Relation` - piensa en ello como una lista inteligente que puede hacer búsquedas, filtros y ordenamiento. Es como una lista normal, pero con superpoderes.

### Filtrando: Encontrando Productos Específicos 🎯

¿Qué pasa si no quieres VER TODOS los productos, sino solo buscar uno específico? Imagina que tienes 1000 productos y solo quieres encontrar los pantalones. Ahí es donde entra `where`.

```irb
store(dev)> Product.where(name: "Pants")
  Product Load (1.5ms)  SELECT "products".* FROM "products" WHERE "products"."name" = 'Pants' /* loading for pp */ LIMIT 11 /*application='Store'*/
=> [#<Product:0x000000012184d858 id: 2, name: "Pants", created_at: "2024-11-09 16:36:01.856751000 +0000", updated_at: "2024-11-09 16:36:01.856751000 +0000">]
```

**¡Perfecto!** 🎉 Le dijiste a Rails: "Solo muéstrame los productos que se llaman 'Pants'" y Rails buscó en la base de datos y solo te devolvió los pantalones.

Mira la consulta SQL que Rails generó: tiene un `WHERE "products"."name" = 'Pants'`. Eso es Rails traduciendo tu petición al idioma de la base de datos. ¡Tú solo escribiste código Ruby simple!

#### Ordenando: Poniendo Productos en Orden 📋

¿Quieres ver tus productos ordenados alfabéticamente? ¡Fácil! Usa `order`:

```irb
store(dev)> Product.order(name: :asc)
  Product Load (0.3ms)  SELECT "products".* FROM "products" /* loading for pp */ ORDER BY "products"."name" ASC LIMIT 11 /*application='Store'*/
=> [#<Product:0x0000000120e02a88 id: 2, name: "Pants", created_at: "2024-11-09 16:36:01.856751000 +0000", updated_at: "2024-11-09 16:36:01.856751000 +0000">,
 #<Product:0x0000000120e02948 id: 1, name: "T-Shirt", created_at: "2024-11-09 16:35:01.117836000 +0000", updated_at: "2024-11-09 16:35:01.117836000 +0000">]
```

¡Mira! Ahora primero aparecen "Pants" y luego "T-Shirt". Están ordenados alfabéticamente (de la A a la Z).

El `:asc` significa "ascendente" (A→Z). Si quisieras al revés (Z→A), usarías `:desc` (descendente).

### Encontrando UN Producto por su ID 🎯

¿Qué pasa si quieres encontrar UN producto específico usando su número de identificación (ID)?

Es como decir: "Dame la ficha del producto #1". Usa el método `find`:

```irb
store(dev)> Product.find(1)
  Product Load (0.2ms)  SELECT "products".* FROM "products" WHERE "products"."id" = 1 LIMIT 1 /*application='Store'*/
=> #<Product:0x000000012054af08 id: 1, name: "T-Shirt", created_at: "2024-11-09 16:35:01.117836000 +0000", updated_at: "2024-11-09 16:35:01.117836000 +0000">
```

**¡Encontrado!** 🎉 Rails buscó el producto con `id = 1` y te lo devolvió.

Nota la diferencia: esta vez NO recibiste una lista (con `[]`), sino UN SOLO producto. Cuando usas `find`, Rails sabe que solo quieres uno.

💡 **¿Por qué funciona así?** Porque cada producto tiene un ID único. Es como el número de cédula: cada persona tiene uno diferente. Cuando buscas por ID, Rails sabe que solo hay un resultado posible.

### Actualizando Productos: Cambiando Información ✏️

¿Qué pasa si te equivocaste en el nombre de un producto o quieres cambiarlo? ¡No hay problema! Puedes actualizarlo.

Hay dos formas de hacerlo, pero la más fácil es usar `update`. Es como borrar algo con corrector y escribir encima:

```irb
store(dev)> product = Product.find(1)
store(dev)> product.update(name: "Shoes")
  TRANSACTION (0.1ms)  BEGIN immediate TRANSACTION /*application='Store'*/
  Product Update (0.3ms)  UPDATE "products" SET "name" = 'Shoes', "updated_at" = '2024-11-09 22:38:19.638912' WHERE "products"."id" = 1 /*application='Store'*/
  TRANSACTION (0.4ms)  COMMIT TRANSACTION /*application='Store'*/
=> true
```

**¡Listo!** ✅ El `=> true` significa "¡Actualización exitosa!"

¿Qué acaba de pasar?
1. Encontraste el producto #1 (la camiseta)
2. Le cambiaste el nombre a "Shoes" (zapatos)
3. Rails lo guardó automáticamente en la base de datos

Nota cómo Rails también actualizó `updated_at` automáticamente. ¡No tuviste que hacer nada! Rails siempre registra cuándo cambias algo.

Vamos a verificar que el cambio se guardó. Pide ver todos los productos de nuevo:

```irb
store(dev)> Product.all
```

**¡Mira!** El producto #1 ahora se llama "Shoes" en lugar de "T-Shirt". El cambio está guardado permanentemente.

```irb
  Product Load (0.3ms)  SELECT "products".* FROM "products" /* loading for pp */ LIMIT 11 /*application='Store'*/
=>
[#<Product:0x000000012c0f7300
  id: 1,
  name: "Shoes",
  created_at: "2024-12-02 20:29:56.303546000 +0000",
  updated_at: "2024-12-02 20:30:14.127456000 +0000">,
 #<Product:0x000000012c0f71c0
  id: 2,
  name: "Pants",
  created_at: "2024-12-02 20:30:02.997261000 +0000",
  updated_at: "2024-12-02 20:30:02.997261000 +0000">]
```

#### Método Alternativo: Cambiar y Luego Guardar

Hay otra forma de actualizar que te da más control. En lugar de usar `update` (que hace todo de una vez), puedes cambiar el valor y luego guardarlo cuando estés lista.

Vamos a cambiar "Shoes" de vuelta a "T-Shirt" usando este método:

```irb
store(dev)> product = Product.find(1)
store(dev)> product.name = "T-Shirt"
=> "T-Shirt"
store(dev)> product.save
  TRANSACTION (0.1ms)  BEGIN immediate TRANSACTION /*application='Store'*/
  Product Update (0.2ms)  UPDATE "products" SET "name" = 'T-Shirt', "updated_at" = '2024-11-09 22:39:09.693548' WHERE "products"."id" = 1 /*application='Store'*/
  TRANSACTION (0.0ms)  COMMIT TRANSACTION /*application='Store'*/
=> true
```

¿Ves la diferencia?
1. **Primer paso:** `product.name = "T-Shirt"` - Solo cambias el valor en la memoria (como escribir en un papel)
2. **Segundo paso:** `product.save` - Ahora SÍ lo guardas en la base de datos

Esta forma es útil cuando quieres hacer varios cambios antes de guardar, o cuando quieres verificar algo antes de guardar definitivamente.

### Eliminando Productos: Borrando de la Base de Datos 🗑️

¿Qué pasa si quieres eliminar un producto completamente? Tal vez lo vendiste todo y ya no lo ofreces, o fue un error.

Para eliminar un producto, usa el método `destroy`. Es como romper una ficha y tirarla a la basura:

```irb
store(dev)> product.destroy
  TRANSACTION (0.1ms)  BEGIN immediate TRANSACTION /*application='Store'*/
  Product Destroy (0.4ms)  DELETE FROM "products" WHERE "products"."id" = 1 /*application='Store'*/
  TRANSACTION (0.1ms)  COMMIT TRANSACTION /*application='Store'*/
=> #<Product:0x0000000125813d48 id: 1, name: "T-Shirt", created_at: "2024-11-09 22:39:38.498730000 +0000", updated_at: "2024-11-09 22:39:38.498730000 +0000">
```

**¡Eliminado!** 🗑️ Mira la consulta SQL: `DELETE FROM "products" WHERE "products"."id" = 1`. Rails le dijo a la base de datos: "Elimina el producto #1".

⚠️ **¡Cuidado!** Cuando eliminas algo con `destroy`, se va PARA SIEMPRE. No hay botón de "deshacer". Así que usa este método con cuidado.

Vamos a verificar que se eliminó. Pide ver todos los productos:

```irb
store(dev)> Product.all
  Product Load (1.9ms)  SELECT "products".* FROM "products" /* loading for pp */ LIMIT 11 /*application='Store'*/
=>
[#<Product:0x000000012abde4c8
  id: 2,
  name: "Pants",
  created_at: "2024-11-09 22:33:19.638912000 +0000",
  updated_at: "2024-11-09 22:33:19.638912000 +0000">]
```

**¡Perfecto!** Ahora solo queda un producto: los pantalones (Pants). La camiseta fue eliminada exitosamente.

### Validaciones: Las Reglas del Juego 🛡️

Imagina que estás llenando un formulario en línea y tratas de enviarlo sin poner tu nombre. El sitio web te dice: "¡Espera! El nombre es obligatorio." Eso es una **validación**.

Las validaciones son reglas que proteges tu base de datos de información mala o incompleta. Son como un guardia de seguridad que revisa que todo esté bien antes de dejar pasar algo.

#### Agregando Tu Primera Validación

Vamos a agregar una regla que diga: "Todos los productos DEBEN tener un nombre. No se permite guardar productos sin nombre."

Abre el archivo `app/models/product.rb` en tu editor y cámbialo para que se vea así:

```ruby
class Product < ApplicationRecord
  validates :name, presence: true
end
```

**¿Qué acabas de escribir?** 🤔

`validates :name, presence: true` significa: "Valida que el campo `name` tenga `presence` (presencia). Debe estar presente, no puede estar vacío."

Es como poner un letrero que dice: "STOP ✋ No puedes pasar sin nombre."

#### Recargando la Consola 🔄

¿Recuerdas que Rails recarga automáticamente los cambios? Bueno, hay UNA excepción: la consola de Rails. Si ya tienes la consola abierta cuando cambias código, necesitas recargarla manualmente.

Es fácil, solo escribe `reload!` en la consola:

```irb
store(dev)> reload!
Reloading...
```

¡Listo! Ahora la consola tiene tu validación nueva cargada.

#### Probando la Validación 🧪

Vamos a ver si la validación funciona. Intentemos crear un producto SIN ponerle nombre y ver qué pasa:

```irb
store(dev)> product = Product.new
store(dev)> product.save
=> false
```

**¡OJO!** 👀 Esta vez `save` devolvió `false` (falso) en lugar de `true`. Eso significa: "No lo guardé. Algo está mal."

¿Por qué? Porque intentaste guardar un producto sin nombre, y tu validación dijo: "¡Alto ahí! Los productos DEBEN tener nombre."

Rails revisa automáticamente las validaciones cada vez que intentas crear (`create`), actualizar (`update`) o guardar (`save`) algo. Si algo viola las reglas, Rails dice "no" y no lo guarda.

#### Viendo los Errores 🔍

¿Quieres saber exactamente QUÉ está mal? Pregúntale al producto sobre sus errores:

```irb
store(dev)> product.errors
=> #<ActiveModel::Errors [#<ActiveModel::Error attribute=name, type=blank, options={}>]>
```

Esto te muestra un objeto `ActiveModel::Errors` - básicamente una lista de todos los errores que tiene este producto. Puedes ver que dice `attribute=name, type=blank` - "El atributo 'name' está en blanco."

#### Mensajes Amigables para Usuarios 💬

Ese mensaje técnico está bien para programadores, pero no es muy amigable para mostrarle a un usuario. ¡Rails puede convertirlo en un mensaje bonito!

```irb
store(dev)> product.errors.full_messages
=> ["Name can't be blank"]
```

**¡Perfecto!** 🌟 "Name can't be blank" (El nombre no puede estar en blanco). Este es un mensaje que puedes mostrarle a un usuario en tu página web. Es claro y fácil de entender.

Las validaciones son súper importantes porque:
- ✅ Protegen tu base de datos de información basura
- ✅ Dan mensajes claros cuando algo está mal
- ✅ Mejoran la experiencia del usuario

**¡Felicidades!** 🎉 Ya dominas los fundamentos de trabajar con la base de datos: crear, leer, actualizar, eliminar y validar. Estos son los bloques de construcción de casi cualquier aplicación web.

#### Saliendo de la Consola

Hemos terminado con la consola por ahora. Para salir, simplemente escribe `exit` y presiona Enter.

Ahora viene algo emocionante: ¡vamos a construir una interfaz web para que las personas puedan ver y crear productos desde un navegador! 🌐

El Viaje de una Petición: ¿Cómo Funciona Todo? 🚂
---------------------------------

¡Ahora viene la parte súper interesante! Vamos a entender cómo funciona todo el sistema cuando alguien visita tu aplicación web.

### La Historia Completa 📖

Imagina que tu aplicación web es como un restaurante. Cuando un cliente (visitante) llega, pasan varias cosas:

1. 🚪 **La Puerta de Entrada (Route)**: El cliente entra y dice "Quiero ver el menú de productos"
2. 🧑‍💼 **El Mesero (Controller)**: Un mesero escucha y dice "¡Entendido! Voy a buscar esa información"
3. 👨‍🍳 **La Cocina (Model)**: El mesero va a la cocina (base de datos) y pide: "Dame todos los productos"
4. 🍽️ **El Plato Bonito (View)**: La cocina da los productos al mesero, quien los presenta en un plato bonito (página HTML)
5. 😊 **El Cliente Ve su Pedido**: ¡El cliente ve la página con todos los productos hermosamente presentados!

### ¿Cómo se Hace en Código?

Para que tu aplicación Rails muestre una página, necesitas crear TRES cosas:

1. 🛤️ **Una Route (Ruta)** - Define qué URLs existen en tu aplicación
2. 🎮 **Un Controller con una Action** - El código que decide qué hacer
3. 🎨 **Una View (Vista)** - El HTML que el usuario ve

**En términos técnicos:**
- Las **routes** son reglas que escribes en Ruby que dicen "si alguien visita /products, mándalo al ProductsController"
- Los **controllers** son clases de Ruby, y sus métodos (llamados "actions") hacen el trabajo
- Las **views** son archivos HTML (con un poco de Ruby mezclado) que crean lo que el usuario ve

Suena complicado, ¿verdad? ¡No te preocupes! Vamos a construirlo paso a paso y verás que es más fácil de lo que parece. 🚀

Routes: El Mapa de Tu Aplicación 🗺️
------

Una **route** (ruta) en Rails es como el directorio de un edificio. Le dice a Rails: "Cuando alguien visite esta dirección, mándalo a este lugar específico."

Antes de crear routes, necesitas entender cómo funcionan las direcciones web (URLs). ¡Es más simple de lo que piensas!

### Anatomía de una URL: Desarmando una Dirección Web 🔍

Mira esta URL:

```
https://example.org/products?sale=true&sort=asc
```

Cada parte tiene un nombre y un propósito. Es como una dirección postal completa:

- 🔒 **`https`** - El **protocolo**: Es como el tipo de transporte (correo normal, correo certificado). Define cómo se envía la información de forma segura.

- 🏢 **`example.org`** - El **host** (anfitrión): Es como el nombre de la ciudad. Dice A QUÉ servidor conectarse.

- 📍 **`/products`** - El **path** (camino): Es como la dirección de la calle. Dice QUÉ página específica quieres dentro del sitio web.

- 🔍 **`?sale=true&sort=asc`** - Los **query parameters** (parámetros de consulta): Es como notas extras. "Muéstrame solo productos en oferta, ordenados alfabéticamente."

Rails se enfoca principalmente en el **path** (`/products`). Esa es la parte que defines en tus routes.

### Métodos HTTP: Los Verbos de Internet 🗣️

Cuando visitas una página web, tu navegador no solo dice "quiero ir a /products". También especifica QUÉ quiere hacer ahí. Esto se llama el **método HTTP**.

Piensa en los métodos HTTP como verbos en una oración:

- **GET** 👀 - "Quiero VER algo"
  - Ejemplo: Ver la lista de productos, ver un producto específico
  - Es como abrir un libro para leer

- **POST** ➕ - "Quiero CREAR algo nuevo"
  - Ejemplo: Agregar un producto nuevo a la tienda
  - Es como agregar una ficha nueva al archivo

- **PATCH/PUT** ✏️ - "Quiero ACTUALIZAR algo existente"
  - Ejemplo: Cambiar el precio de un producto
  - Es como borrar y reescribir en una ficha

- **DELETE** 🗑️ - "Quiero ELIMINAR algo"
  - Ejemplo: Quitar un producto de la tienda
  - Es como tirar una ficha a la basura

Estos cuatro métodos se usan para todo en la web. ¡Son como los bloques fundamentales de construcción!

### Creando Tu Primera Route en Rails 🛤️

Una **route** en Rails conecta tres cosas:
1. Un método HTTP (GET, POST, etc.)
2. Una URL (como `/products`)
3. Un controller y una action (el código que responde)

Es como decir: "Cuando alguien haga un GET a /products, mándalo al ProductsController, método index."

¡Vamos a crear tu primera route! Abre el archivo `config/routes.rb` en tu editor y agrega esto:

```ruby
Rails.application.routes.draw do
  get "/products", to: "products#index"
end
```

**¡Vamos a descifrar esto!** 🔍

- `get` - El método HTTP. "Esta route responde a peticiones GET"
- `"/products"` - El path. "Cuando alguien visite /products..."
- `to: "products#index"` - "...mándalo al ProductsController, action index"

El `products#index` usa una notación especial:
- `products` = ProductsController (Rails agrega "Controller" automáticamente)
- `#` = separador
- `index` = el método (action) dentro del controller

Cuando alguien visite tu sitio y vaya a `/products`, Rails:
1. ✅ Ve que hay una route que coincide
2. ✅ Busca el ProductsController
3. ✅ Llama al método `index`
4. ✅ El controller hace su trabajo y devuelve una respuesta

💡 **¿Por qué no ponemos `https://` o el nombre del dominio?** Porque Rails ya sabe que la petición llegó a TU servidor. El protocolo (`https://`) y el dominio (`mitienda.com`) solo sirven para que la petición llegue a tu aplicación. Una vez ahí, Rails solo necesita saber el path (`/products`) para decidir qué hacer.
Los **query parameters** (esos `?sale=true&sort=asc`) son como opciones extra que puedes usar en el controller para filtrar o modificar los datos. Por ejemplo, "muéstrame solo productos en oferta, ordenados alfabéticamente."

<picture class="flowdiagram">
  <source srcset="/assets/images/guides/routing_dark.jpg" media="(prefers-color-scheme:dark)">
  <img src="/assets/images/guides/routing_light.jpg">
</picture>

#### Agregando Más Routes

Vamos a agregar otra route. Esta vez para CREAR productos nuevos. Agrega esta línea después de la route anterior en `config/routes.rb`:

```ruby
post "/products", to: "products#create"
```

¿Ves la diferencia? Esta route usa `post` en lugar de `get`.

- La primera route (`get "/products"`) es para VER productos
- Esta route (`post "/products"`) es para CREAR un producto nuevo

Ambas usan la misma URL (`/products`), ¡pero Rails las distingue por el método HTTP! Es como tener dos puertas en el mismo lugar: una dice "Entrada para ver" y otra dice "Entrada para crear."

#### URLs Dinámicas: Capturando Información 🎯

Ahora viene algo cool. ¿Qué pasa si quieres ver UN producto específico? Como ver el producto #5 o el producto #10?

No puedes crear una route diferente para cada producto (¡imagina tener 1000 routes!). En su lugar, usas **parámetros dinámicos**:

```ruby
get "/products/:id", to: "products#show"
```

**¡Mira ese `:id`!** 🎯 Eso es un **parámetro dinámico**. Los dos puntos (`:`) le dicen a Rails: "Esta parte puede cambiar."

Funciona así:
- Alguien visita `/products/1` → Rails captura `1` y lo guarda como el parámetro `id`
- Alguien visita `/products/5` → Rails captura `5` como el `id`
- Alguien visita `/products/999` → Rails captura `999` como el `id`

Es como un formulario con un espacio en blanco: "Muéstrame el producto número ____". El número que pongas en el espacio se convierte en el parámetro `id`.

Luego, en el controller, puedes usar ese `id` para buscar el producto específico en la base de datos con `Product.find(id)`. ¡Súper útil!

💡 **¿Solo números?** ¡No! Los parámetros pueden ser cualquier cosa. Por ejemplo, imagina un blog:

```ruby
get "/blog/:title", to: "blog#show"
```

Si visitas `/blog/hello-world`, Rails captura `hello-world` como el parámetro `title`. Luego puedes buscar el artículo del blog con ese título. ¡Las posibilidades son infinitas!

#### Las 8 Routes Mágicas de CRUD ✨

¿Recuerdas CRUD? **C**reate (Crear), **R**ead (Leer), **U**pdate (Actualizar), **D**elete (Eliminar). Son las 4 operaciones básicas para cualquier cosa en una base de datos.

Para que CRUD funcione completamente en una aplicación web, necesitas **8 routes**. Suena como mucho, pero cada una tiene un propósito claro:

**Para VER cosas (Read - Leer):**

1. 📋 **Index** - Muestra TODOS los productos (lista completa)
2. 👁️ **Show** - Muestra UN producto específico (detalles de uno solo)

**Para CREAR cosas (Create - Crear):**

3. 📝 **New** - Muestra el formulario para crear un producto nuevo
4. ➕ **Create** - Procesa el formulario y guarda el producto en la base de datos

**Para ACTUALIZAR cosas (Update - Actualizar):**

5. ✏️ **Edit** - Muestra el formulario para editar un producto existente
6. 🔄 **Update** - Procesa el formulario y actualiza el producto en la base de datos

**Para ELIMINAR cosas (Delete - Eliminar):**

7. 🗑️ **Destroy** - Elimina un producto de la base de datos

Así se ven todas las routes juntas:

```ruby
get "/products", to: "products#index"

get "/products/new", to: "products#new"
post "/products", to: "products#create"

get "/products/:id", to: "products#show"

get "/products/:id/edit", to: "products#edit"
patch "/products/:id", to: "products#update"
put "/products/:id", to: "products#update"

delete "/products/:id", to: "products#destroy"
```

**¡WOW!** Eso es mucho código. Son 9 líneas (con línea en blanco entre grupos) para definir las 8 routes CRUD.

#### El Atajo Mágico: Resources 🪄

Aquí viene la mejor parte. Los programadores de Rails pensaron: "Escribir estas 8 routes una y otra vez es aburrido y repetitivo. ¡Hagamos un atajo!"

¿Listo? Puedes reemplazar TODAS esas 9 líneas con UNA SOLA línea mágica:

```ruby
resources :products
```

**¡INCREÍBLE!** 🎉 Una línea de código = 8 routes completas. Esto es **Convention over Configuration** en acción. Rails asume que si tienes un recurso llamado "products", probablemente quieres las 8 routes CRUD estándar.

Cambia tu archivo `config/routes.rb` para usar `resources :products` en lugar de todas esas líneas individuales. ¡Ahorrarás un montón de espacio!

💡 **¿Y si no quieres todas las 8 routes?** Puedes especificar exactamente cuáles necesitas. Consulta la [guía de routing](https://guides.rubyonrails.org/routing.html) para aprender más trucos cool.

### Viendo Todas Tus Routes: El Comando Mágico 🔍

¿Quieres ver TODAS las routes que existen en tu aplicación? Rails tiene un comando para eso.

En tu terminal, escribe:

```bash
$ bin/rails routes
```

Rails te mostrará una tabla hermosa con todas tus routes. Verás algo como esto:

```
      Prefix Verb   URI Pattern                  Controller#Action
    products GET    /products(.:format)          products#index
             POST   /products(.:format)          products#create
 new_product GET    /products/new(.:format)      products#new
edit_product GET    /products/:id/edit(.:format) products#edit
     product GET    /products/:id(.:format)      products#show
             PATCH  /products/:id(.:format)      products#update
             PUT    /products/:id(.:format)      products#update
             DELETE /products/:id(.:format)      products#destroy
```

**¡Mira!** Ahí están las 8 routes que `resources :products` creó automáticamente. La tabla te muestra:
- **Prefix**: Un nombre corto para la route (útil para crear links)
- **Verb**: El método HTTP (GET, POST, etc.)
- **URI Pattern**: La URL que coincide
- **Controller#Action**: A dónde va la petición

También verás otras routes que Rails agrega automáticamente, como health checks (verificaciones de salud del servidor).

💡 **Consejo pro:** Este comando es súper útil cuando te olvidas qué routes existen o cómo se llaman exactamente. ¡Guárdalo en tu memoria!

Controllers & Actions: El Cerebro de Tu Aplicación 🧠
---------------------

¡Perfecto! Ya tienes routes. Ahora necesitas el **Controller** - el "mesero" que recibe las peticiones y decide qué hacer.

### Generando el Controller

Rails tiene (otra vez) un comando mágico para crear controllers. Vamos a generar un `ProductsController` con la action `index`.

En tu terminal, escribe:

```bash
$ bin/rails generate controller Products index --skip-routes
      create  app/controllers/products_controller.rb
      invoke  erb
      create    app/views/products
      create    app/views/products/index.html.erb
      invoke  test_unit
      create    test/controllers/products_controller_test.rb
      invoke  helper
      create    app/helpers/products_helper.rb
      invoke    test_unit
```

**¿Qué acabas de hacer?** 🎯

Vamos a desglosar el comando:
- `generate controller` - "Rails, genera un controller"
- `Products` - Llámalo ProductsController (Rails agrega "Controller" automáticamente)
- `index` - Crea una action llamada `index` dentro del controller
- `--skip-routes` - No agregues routes (ya las tenemos con `resources :products`)

**¡Mira todo lo que Rails creó!** 🎁

Rails acaba de generar varios archivos automáticamente:
- 📄 **El controller** en `app/controllers/products_controller.rb` - El código que maneja las peticiones
- 📁 **Una carpeta de views** en `app/views/products/` - Donde van los archivos HTML
- 🎨 **Un archivo de view** `index.html.erb` - La página HTML para la action index
- 🧪 **Archivos de prueba** - Para verificar que todo funcione (los veremos después)
- 🤝 **Un helper** - Funciones auxiliares que puedes usar en las views

¡Rails hizo TODO eso con un solo comando! Es como ordenar una casa prefabricada que llega lista para habitar.
* Un archivo de test para este controller
* Un archivo helper para extraer lógica en nuestras views

¡Ahora viene la parte emocionante! 🎯 Vamos a abrir el ProductsController que Rails creó para nosotras. Búscalo en `app/controllers/products_controller.rb`. Cuando lo abras, verás algo así:

```ruby
class ProductsController < ApplicationController
  def index
  end
end
```

💡 **Dato curioso sobre los nombres:** ¿Te diste cuenta de algo interesante? El nombre del archivo es `products_controller.rb` (con guiones bajos), pero la clase se llama `ProductsController` (en formato CamelCase, como un camello con jorobas 🐫).

Esto no es casualidad. Es una de las convenciones de Rails que hace que todo funcione mágicamente. Rails sabe automáticamente que cuando necesita el archivo `ProductsController`, debe buscar el archivo `products_controller.rb`. ¡Es como si Rails supiera leer tu mente! No necesitas decirle dónde encontrar las cosas porque sigue reglas predecibles.

Ahora fíjate en el método `index` dentro del controller. ✨ En el mundo de Rails, este tipo de método se llama una **Action** (Acción). Una action es como una tarea específica que el controller sabe hacer.

Piensa en el controller como un mesero en un restaurante, y cada action es un tipo de servicio que puede ofrecer:
- La action `index` es como cuando pides ver el menú completo
- La action `show` sería ver un platillo específico
- La action `create` sería hacer un pedido nuevo

¿Ves que el método `index` está vacío? ¡No tiene ni una línea de código! Pero aquí viene la magia de Rails: 🪄 **Incluso vacío, funciona**.

¿Por qué? Porque Rails es súper inteligente. Cuando ve una action vacía, automáticamente busca y muestra el archivo de vista (view) que tiene el mismo nombre.

En este caso, la action `index` renderizará (mostrará) el archivo `app/views/products/index.html.erb`. Si abres ese archivo en tu editor de código, verás el HTML que Rails va a mostrar en el navegador.

```erb
<h1>Products#index</h1>
<p>Find me in app/views/products/index.html.erb</p>
```

### 🌐 Haciendo Peticiones (¡Vamos a Ver Todo en Acción!)

¡Es hora de ver tu trabajo en el navegador! 🎉 Esta es una de las partes más emocionantes porque vas a ver cómo todo lo que has aprendido trabaja junto.

**Paso 1:** Primero, ejecuta `bin/rails server` en tu terminal para iniciar el servidor Rails (tu "cocina" donde se preparan las páginas web).

**Paso 2:** Luego abre la URL de tu Codespace y verás la página de bienvenida de Rails.

💡 **Recuerda:** En GitHub Codespaces, tu aplicación no se ejecuta en `localhost:3000` sino en una URL única generada automáticamente. Para encontrar tu URL, ve a la pestaña "PORTS" (Puertos) en la parte inferior del editor de Codespaces, busca el puerto 3000 en la lista, y copia la URL que aparece en la columna "Forwarded Address". Esta URL tendrá un formato similar a `https://TU-CODESPACE.github.dev`. Usa esta URL cada vez que la guía mencione acceder a la aplicación.

**Paso 3:** Ahora, abre https://TU-CODESPACE.github.dev/products en tu navegador. ¡Verás la página que Rails renderizó para products index!

#### 🎬 ¿Qué Acaba de Pasar? (El Viaje de una Petición)

Déjame contarte la historia de lo que sucedió en segundo cuando visitaste `/products`. Es como una cadena de eventos perfectamente coordinada:

1. **Tu navegador pidió:** "Quiero ver `/products`"
2. **El Router de Rails dijo:** "¡Ah! Conozco ese camino. Eso es `products#index`"
3. **Rails envió la petición al ProductsController** y le dijo: "¡Oye! Necesito que ejecutes tu action `index`"
4. **La action index se ejecutó** (aunque está vacía, así que no hizo mucho)
5. **Rails pensó:** "Hmm, la action está vacía. Voy a renderizar automáticamente el template que coincide con este nombre"
6. **Rails encontró y renderizó** `app/views/products/index.html.erb`
7. **El HTML final fue enviado** de vuelta a tu navegador
8. **¡Tu navegador mostró la página!** 🎉

¿Ves cómo todo el patrón MVC trabajó en conjunto? Router → Controller → View. ¡Todo conectado como una máquina bien aceitada!

#### 🏠 Configurando la Página de Inicio

¿Qué tal si hacemos que la página de productos sea lo primero que ven las personas cuando visitan tu sitio? Es como decidir qué poner en la puerta principal de tu tienda.

Abre el archivo `config/routes.rb` y agreguemos una línea que le dice a Rails: "Cuando alguien visite la página principal (la raíz), muéstrale la lista de productos". Agrega esta línea:

```ruby
root "products#index"
```

¡Listo! 🎊 Ahora cuando visites https://TU-CODESPACE.github.dev (sin agregar `/products` al final), Rails automáticamente te mostrará la lista de productos. ¡Es como si dijeras "esta es mi página de bienvenida"!

### 📦 Variables de Instancia (El Puente entre Controller y View)

¡Ahora viene algo súper interesante! Vamos a hacer que nuestra página muestre datos reales de la base de datos. 🎯

Imagina que el Controller es como un asistente que va a buscar información, y la View es como una artista que la presenta bonita. ¿Cómo le pasa el asistente la información a la artista? ¡Con las **variables de instancia**!

Las variables de instancia son fáciles de reconocer porque **siempre empiezan con el símbolo @**. Son como cajas con una etiqueta especial que pueden viajar del Controller a la View.

Vamos a crear una variable de instancia en la action `index` para traer todos los productos de la base de datos:

```ruby
class ProductsController < ApplicationController
  def index
    @products = Product.all
  end
end
```

Mira esa línea `@products = Product.all`. Le estamos diciendo: "Ve a la base de datos, trae TODOS los productos, y guárdalos en esta caja llamada `@products`". ✨

Ahora, para ver qué hay en esa caja, vamos a usar algo llamado ERB en nuestra vista. Abre `app/views/products/index.html.erb` y reemplaza el contenido con esto:

```erb
<%= debug @products %>
```

#### 🎨 ¿Qué es ERB?

**ERB** significa "Embedded Ruby" (Ruby Incrustado). Es como una forma mágica de mezclar código Ruby con HTML. ✨

Piensa en ello así: normalmente el HTML es estático (siempre muestra lo mismo), pero con ERB puedes hacer que sea dinámico (que cambie dependiendo de los datos).

Las etiquetas especiales de ERB son:
- **`<%= %>`** → "Ejecuta este código Ruby Y MUESTRA el resultado en la página"
- **`<% %>`** → "Ejecuta este código Ruby pero NO muestres el resultado" (ya veremos esto en un momento)

En nuestro caso, `<%= debug @products %>` le dice a Rails:
1. Toma lo que hay en `@products`
2. Conviértelo a un formato legible (YAML)
3. Muéstralo en la página

Ahora actualiza https://TU-CODESPACE.github.dev/ en tu navegador. ¡Wow! 😮 ¿Ves que la salida cambió? Lo que estás viendo son todos los productos de tu base de datos mostrados en formato YAML (un formato que es fácil de leer para humanos).

💡 **¿Para qué sirve el helper `debug`?**

El `debug` es como una lupa 🔍 que te ayuda a ver exactamente qué hay dentro de tus variables. Es súper útil cuando algo no funciona como esperabas.

Por ejemplo, imagina que por error escribiste `@product` (singular) en lugar de `@products` (plural). Con el helper debug verías que la variable está vacía y pensarías: "¡Ah! Me equivoqué en el nombre de la variable en el controller".

Es como tener un detective que te ayuda a encontrar problemas. Los programadores profesionales usan herramientas como esta todo el tiempo.

✨ **Dato curioso:** Rails tiene muchos helpers (ayudantes) que hacen tu vida más fácil. Si quieres conocer más, consulta la [guía de Action View Helpers](https://guides.rubyonrails.org/action_view_helpers.html).

#### 🎯 Mostrando la Lista de Productos de Forma Bonita

El formato YAML está bien para depurar, pero queremos que nuestra página se vea bonita para los usuarios. ¡Vamos a mejorar esto!

Actualiza `app/views/products/index.html.erb` para mostrar todos los nombres de productos de una forma más presentable:

```erb
<h1>Products</h1>

<div id="products">
  <% @products.each do |product| %>
    <div>
      <%= product.name %>
    </div>
  <% end %>
</div>
```

#### 🔄 Entendiendo el Código

¡Vamos a desglosar este código línea por línea para que entiendas la magia que está pasando!

```
<% @products.each do |product| %>
```

Esta línea dice: "Para cada producto en mi colección de `@products`, haz lo siguiente...". Es como decir: "Para cada libro en mi estantería, voy a leer el título".

Fíjate que usamos `<% %>` (sin el signo `=`). ¿Recuerdas la diferencia?
- `<% %>` = "Ejecuta el código pero NO lo muestres"
- `<%= %>` = "Ejecuta el código Y MUÉSTRALO"

No queremos mostrar el código del loop, solo queremos que se ejecute. Por eso no lleva el `=`.

```
<%= product.name %>
```

Aquí SÍ usamos `<%= %>` porque queremos mostrar el nombre del producto en la página.

```
<% end %>
```

Y esta línea cierra el loop diciendo "ya terminé de recorrer todos los productos".

**En resumen:** Este código toma cada producto de tu base de datos y crea un `<div>` con su nombre. ¡Es como crear una tarjeta para cada producto automáticamente! 🎴

### 🎯 Actions CRUD (¡Vamos a Completar las Operaciones!)

Hasta ahora podemos ver la lista completa de productos. ¡Eso es genial! 🎉 Pero ¿qué tal si queremos ver los detalles de UN producto específico? Aquí es donde entra la **R** de CRUD (Read - Leer un recurso individual).

¿Recuerdas que cuando usamos `resources :products` en las rutas, Rails creó automáticamente 8 rutas mágicas? Una de esas rutas es `/products/:id` que apunta a `products#show`.

Esa ruta ya existe, pero aún no hemos creado la action `show` en nuestro controller. ¡Vamos a hacerlo!

### 🔍 Mostrando Productos Individuales

Abre el controller Products y agrega la action `show` así:

```ruby
class ProductsController < ApplicationController
  def index
    @products = Product.all
  end

  def show
    @product = Product.find(params[:id])
  end
end
```

#### 📝 Entendiendo la Action Show

Mira el código que acabamos de agregar. Hay cosas interesantes aquí:

**1. Singular vs Plural:**
- En `index` usamos `@products` (plural) porque traemos TODOS los productos
- En `show` usamos `@product` (singular) porque traemos UN solo producto

Es como la diferencia entre decir "trae todos los libros" vs "trae EL libro".

**2. ¿Qué es `params`?**

`params` es como una mochila mágica 🎒 que contiene información que viene en la petición (request). Cuando alguien visita `/products/1`, Rails automáticamente pone `{id: 1}` en esa mochila.

Entonces cuando escribimos `params[:id]`, es como decir: "Mira en la mochila y dame el valor del `id`".

**3. El Flujo Completo:**

Imagina que alguien visita `https://TU-CODESPACE.github.dev/products/1`:
1. Rails ve el `1` en la URL y lo guarda en `params[:id]`
2. La action `show` se ejecuta
3. `Product.find(params[:id])` se convierte en `Product.find(1)`
4. Rails busca en la base de datos el producto con ID 1
5. Lo guarda en `@product`
6. Esa variable viaja a la vista para mostrarse

¡Es como un tren de información! 🚂

#### 🎨 Creando la Vista para Show

Ahora necesitamos crear la vista (view) para mostrar un producto individual. ¿Recuerdas las convenciones de Rails? Son como reglas que, si las sigues, todo funciona mágicamente.

Rails espera que:
- Las views del `ProductsController` estén en la carpeta `app/views/products`
- La view para la action `show` se llame `show.html.erb`

Entonces, crea un nuevo archivo en `app/views/products/show.html.erb` y agrega este contenido:

```erb
<h1><%= @product.name %></h1>

<%= link_to "Back", products_path %>
```

¡Mira ese código! `<%= @product.name %>` muestra el nombre del producto, y `<%= link_to "Back", products_path %>` crea un enlace para regresar a la lista de productos.

#### 🔗 Conectando las Páginas

Sería súper útil que cuando veas la lista de productos, puedas hacer clic en cualquiera para ver sus detalles, ¿verdad? ¡Vamos a agregar esos enlaces!

Actualiza `app/views/products/index.html.erb` para que cada nombre de producto sea un enlace clickeable:

```erb#6,8
<h1>Products</h1>

<div id="products">
  <% @products.each do |product| %>
    <div>
      <a href="/products/<%= product.id %>">
        <%= product.name %>
      </a>
    </div>
  <% end %>
</div>
```

¡Perfecto! 🎉 Si actualizas la página en tu navegador, verás que funciona. Cada nombre de producto ahora es un enlace clickeable.

Pero espera... hay una forma MÁS elegante de hacer esto usando los helpers mágicos de Rails.

#### ✨ Route Helpers: La Forma Elegante de Rails

¿Recuerdas cuando ejecutaste `bin/rails routes`? Además de mostrarte las rutas, también te mostraba una columna llamada "Prefix" (Prefijo). Ese prefijo no está ahí solo para verse bonito... ¡es súper útil!

```
  Prefix Verb   URI Pattern             Controller#Action
products GET    /products(.:format)     products#index
 product GET    /products/:id(.:format) products#show
```

Rails automáticamente crea helpers (ayudantes) basados en esos prefijos. Mira estos ejemplos mágicos:

* `products_path` → genera `"/products"`
* `products_url` → genera `"https://TU-CODESPACE.github.dev/products"`
* `product_path(1)` → genera `"/products/1"`
* `product_url(1)` → genera `"https://TU-CODESPACE.github.dev/products/1"`

#### 🤔 ¿Cuál es la diferencia entre `_path` y `_url`?

**`_path`** (con path):
- Genera una ruta relativa (solo la parte después del dominio)
- Ejemplo: `"/products"`
- Usa esto cuando estás dentro de tu aplicación (enlaces internos)
- Es como decir "ve al cuarto de al lado" sin especificar toda la dirección de la casa

**`_url`** (con url):
- Genera la URL completa (con https:// y todo)
- Ejemplo: `"https://TU-CODESPACE.github.dev/products"`
- Usa esto para emails o cuando necesitas la URL completa
- Es como dar la dirección completa de tu casa: calle, número, ciudad, etc.

**Regla general:** Usa `_path` para enlaces dentro de tu app, y `_url` para emails o compartir fuera de la app. 💡

#### 🔗 El Helper `link_to`

Ahora que conocemos los route helpers, podemos usar el helper `link_to` para crear enlaces de forma súper elegante.

`link_to` es como un asistente que crea enlaces HTML por ti. Le das dos cosas:
1. **El texto que quieres mostrar** (por ejemplo: `product.name`)
2. **A dónde debe llevar el enlace** (por ejemplo: `product_path(product.id)`)

¡Y listo! Rails crea automáticamente una etiqueta `<a>` con todo lo necesario.

Vamos a refactorizar (mejorar) nuestro código usando estos helpers mágicos:

```erb#6
<h1>Products</h1>

<div id="products">
  <% @products.each do |product| %>
    <div>
      <%= link_to product.name, product_path(product.id) %>
    </div>
  <% end %>
</div>
```

### ➕ Creando Products (¡La Letra C de CRUD!)

Hasta ahora, si querías crear productos tenías que hacerlo en la consola de Rails (usando `rails console`). ¡Pero eso no es muy práctico para los usuarios! Vamos a hacer que puedan crear productos directamente desde el navegador usando un formulario. 📝

Para crear productos necesitamos DOS actions que trabajan en equipo:

1. **`new`** → Muestra el formulario vacío para llenar
2. **`create`** → Guarda el producto en la base de datos cuando presionas "Submit"

Es como cuando llenas un formulario en papel (eso es `new`) y luego lo entregas para que lo archiven (eso es `create`).

Comencemos agregando la action `new` en el controller:

```ruby
class ProductsController < ApplicationController
  def index
    @products = Product.all
  end

  def show
    @product = Product.find(params[:id])
  end

  def new
    @product = Product.new
  end
end
```

Mira lo que hace la action `new`: crea un nuevo objeto Product con `Product.new` y lo guarda en `@product`. Este objeto está vacío (como un formulario en blanco), pero Rails lo usa para saber qué campos debe mostrar en el formulario.

Ahora agreguemos un enlace en la página de index para llegar a este formulario. Actualiza `app/views/products/index.html.erb`:

```erb#3
<h1>Products</h1>

<%= link_to "New product", new_product_path %>

<div id="products">
  <% @products.each do |product| %>
    <div>
      <%= link_to product.name, product_path(product.id) %>
    </div>
  <% end %>
</div>
```

¡Perfecto! Ahora tenemos un botón "New product" en la lista. 🎊

Ahora creemos la vista para el formulario. Crea el archivo `app/views/products/new.html.erb` con este contenido:

```erb
<h1>New product</h1>

<%= form_with model: @product do |form| %>
  <div>
    <%= form.label :name %>
    <%= form.text_field :name %>
  </div>

  <div>
    <%= form.submit %>
  </div>
<% end %>

<%= link_to "Cancel", products_path %>
```

#### 📋 El Mágico Helper `form_with`

¡Wow! Mira ese código del formulario. Parece súper simple, ¿verdad? Solo unas pocas líneas, pero Rails hace MUCHA magia detrás de escena.

`form_with model: @product` le dice a Rails: "Crea un formulario para este producto". Rails automáticamente:
- 🔒 Agrega seguridad (tokens CSRF para proteger contra ataques)
- 🎯 Sabe a qué URL enviar los datos (a `/products` para crear)
- 🏷️ Nombra los campos correctamente
- ✨ Hasta cambia el texto del botón ("Create Product" porque es nuevo)

Es como tener un asistente súper inteligente que entiende exactamente lo que necesitas.

Si abres esta página en tu navegador y ves el código fuente (clic derecho → "Ver código fuente"), el HTML generado se ve así:

```html
<form action="/products" accept-charset="UTF-8" method="post">
  <input type="hidden" name="authenticity_token" value="UHQSKXCaFqy_aoK760zpSMUPy6TMnsLNgbPMABwN1zpW-Jx6k-2mISiF0ulZOINmfxPdg5xMyZqdxSW1UK-H-Q" autocomplete="off">

  <div>
    <label for="product_name">Name</label>
    <input type="text" name="product[name]" id="product_name">
  </div>

  <div>
    <input type="submit" name="commit" value="Create Product" data-disable-with="Create Product">
  </div>
</form>
```

¿Ves todas esas cosas que Rails agregó automáticamente? 😮

- **`authenticity_token`** → Es como un código secreto que protege tu aplicación de hackers
- **`method="post"`** → Le dice al navegador que envíe los datos usando el método HTTP POST
- **`name="product[name]"`** → Los nombres de los campos están organizados perfectamente
- **`value="Create Product"`** → El botón tiene el texto correcto automáticamente

¡Todo eso lo hizo Rails! Tú solo escribiste unas pocas líneas simples de ERB.

🤔 **¿Por qué funciona esto?** Porque le pasamos `model: @product` (un producto nuevo), Rails es lo suficientemente inteligente para decir: "Ah, este es un producto nuevo, entonces el formulario debe hacer POST a `/products` para crear uno nuevo". ¡Convención sobre configuración en acción!

#### 💾 Creando la Action `create`

Ahora nuestro formulario está listo, pero cuando alguien presione "Submit", necesitamos una action en el controller que reciba los datos y los guarde. Agrega la action `create` al controller:

```ruby#14-26
class ProductsController < ApplicationController
  def index
    @products = Product.all
  end

  def show
    @product = Product.find(params[:id])
  end

  def new
    @product = Product.new
  end

  def create
    @product = Product.new(product_params)
    if @product.save
      redirect_to @product
    else
      render :new, status: :unprocessable_entity
    end
  end

  private
    def product_params
      params.expect(product: [ :name ])
    end
end
```

#### 🛡️ Strong Parameters (¡Seguridad Importante!)

Mira la última parte del código. Hay algo súper importante de seguridad llamado **Strong Parameters**.

Fíjate que hay un método privado llamado `product_params`:

```ruby
def product_params
  params.expect(product: [ :name ])
end
```

¿Para qué sirve esto? Es como un guardia de seguridad en la entrada de un club. 🚨

**El problema:** Imagina que alguien malicioso intenta enviar datos extra al formulario, como intentar cambiar su rol a "administrador" o modificar el precio de los productos. ¡Eso sería un desastre!

**La solución:** Strong Parameters le dice a Rails: "Solo acepta estos parámetros específicos y NADA más".

En nuestro caso:
- `product:` → Debe venir un objeto product
- `[ :name ]` → Solo permitimos el campo `name`
- Cualquier otro campo será ignorado automáticamente

Es como decir: "Oye, del formulario solo voy a aceptar el nombre del producto. Si alguien intenta enviar otra cosa, ignóralo". 🔒

**¡Este es un patrón de seguridad súper importante que usan todos los programadores profesionales de Rails!**

#### ✅❌ Manejando Errores (¿Se Guardó o No?)

Ahora fíjate en la lógica de la action `create`. Hay un `if` muy importante:

```ruby
if @product.save
  redirect_to @product
else
  render :new, status: :unprocessable_entity
end
```

Vamos a desglosar esto paso a paso:

**1. `@product.save` - Intenta guardar**

Cuando ejecutas `save`, Rails hace DOS cosas:
- Ejecuta las validaciones (¿el nombre está presente?)
- Si todo está bien, guarda en la base de datos

`save` devuelve `true` si tuvo éxito, o `false` si algo salió mal.

**2. Si tuvo éxito (`if @product.save`)**

```ruby
redirect_to @product
```

¡Celebración! 🎉 El producto se guardó. Entonces redirigimos al usuario a la página de detalles del producto.

Aquí hay más magia de Rails: cuando le das un objeto a `redirect_to`, Rails automáticamente sabe que debe ir a la ruta `show` de ese producto. Es como decir `redirect_to product_path(@product.id)`, pero más corto.

**3. Si falló (`else`)**

```ruby
render :new, status: :unprocessable_entity
```

Si las validaciones fallaron (por ejemplo, dejaron el nombre vacío), NO guardamos el producto. En lugar de redirigir, volvemos a mostrar el formulario (`:new`) para que el usuario pueda corregir los errores.

Es como cuando llenas un formulario mal en una oficina y te dicen "falta esto, llénalo de nuevo". 📝

Nota que usamos `render :new` (no `redirect_to`). **Render** muestra la misma vista (`new.html.erb`) pero mantiene los datos que el usuario ya escribió en `@product`. Así el usuario puede ver qué escribió y corregir el error sin tener que empezar de cero.

También establecemos el estado HTTP en `422 Unprocessable Entity` (Entidad No Procesable). Es un código que le dice al navegador: "Recibí los datos pero no pude procesarlos porque tienen errores".

#### 💬 Mensajes de Confirmación: ¡Hablándole al Usuario!

¿Alguna vez has comprado algo en línea y después de hacer clic en "Comprar", aparece un mensaje verde que dice "¡Tu pedido ha sido confirmado!"? O cuando te registras en un sitio web y ves "¡Bienvenida! Tu cuenta ha sido creada". Esos mensajes son súper importantes porque le confirman al usuario que su acción fue exitosa.

**Sin esos mensajes, ¿cómo sabríamos si algo funcionó?** Imagina hacer clic en "Guardar" y... nada. La página cambia pero no sabes si se guardó o no. ¡Sería confuso y frustrante! 😰

Por eso las aplicaciones profesionales siempre le hablan al usuario. Y Rails tiene una herramienta perfecta para esto: **el Flash**.

#### ¿Qué es el Flash? ⚡

El **Flash** es como una **nota adhesiva temporal** que le pasas al usuario. Imagina esto:

1. El usuario crea un producto
2. El controller guarda el producto en la base de datos
3. Antes de redirigir, el controller pega una "nota adhesiva" que dice "¡Producto creado exitosamente!"
4. El usuario es redirigido a otra página
5. Esa página detecta la nota adhesiva y la muestra
6. **Después de mostrarla una vez, la nota desaparece** ✨

Es **temporal** - aparece solo una vez y luego se borra automáticamente. No se queda ahí molestando para siempre.

El [Flash](https://api.rubyonrails.org/classes/ActionDispatch/Flash.html) proporciona una forma de pasar datos temporales entre actions del controller. Cualquier cosa que coloques en el flash estará disponible para la siguiente action y luego se limpiará.

#### Los Dos Tipos de Mensajes 📬

El flash típicamente se usa para dos tipos de mensajes:

**✅ Notice (Avisos Positivos)**
Son mensajes de confirmación cuando algo salió bien:
- "Producto creado exitosamente"
- "Cambios guardados"
- "Bienvenido de vuelta"

Piensa en ellos como una palmadita en la espalda. 🎉

**⚠️ Alert (Alertas y Advertencias)**
Son mensajes cuando algo salió mal o requiere atención:
- "No tienes permiso para hacer eso"
- "Debes iniciar sesión primero"
- "El producto no pudo ser eliminado"

Son como una luz amarilla de precaución. 🚨

#### Agregando un Mensaje de Confirmación a Nuestro Controller

¿Recuerdas nuestra action `create` que guardaba productos? Actualmente, cuando guardamos un producto exitosamente, solo redirigimos al usuario:

```ruby
redirect_to @product
```

Esto funciona, pero no le dice nada al usuario. ¡Agreguemos un mensaje de confirmación! Modifica tu `create` action en `app/controllers/products_controller.rb` así:

```ruby
def create
  @product = Product.new(product_params)
  if @product.save
    redirect_to @product, notice: "Product created successfully!"
  else
    render :new, status: :unprocessable_entity
  end
end
```

¿Ves lo que agregamos? 👀

```ruby
redirect_to @product, notice: "Product created successfully!"
```

Esto le dice a Rails: "Redirige al usuario a la página del producto Y establece un mensaje flash de tipo 'notice' con el texto 'Product created successfully!'"

El argumento `notice:` es un atajo conveniente. También podrías escribir `flash[:notice] = "..."` pero Rails nos da esta forma más corta y elegante. ✨

#### Mostrando los Mensajes en Nuestro Layout 🎨

Perfecto, ahora el controller está creando el mensaje... ¡pero nadie lo está mostrando! Es como escribir una carta y no enviarla. 📮

Necesitamos decirle a nuestras vistas: "Oye, si hay un mensaje flash, muéstralo".

¿Pero en qué vista lo ponemos? ¿En `show.html.erb`? ¿En `new.html.erb`? ¿En todas? 🤔

Aquí viene algo cool: recuerda que dijimos que hay una carpeta `app/views/layouts/`? El **layout** es como la plantilla maestra de tu aplicación. Es el marco que rodea TODAS tus páginas.

Piénsalo como el marco de un cuadro:
- El marco (layout) es siempre el mismo
- El contenido del cuadro (tus vistas) cambia

Si pones el flash en el layout, ¡automáticamente aparecerá en TODAS las páginas! Súper eficiente. 🎯

Abre el archivo `app/views/layouts/application.html.erb` y busca el `<body>`. Justo después de la etiqueta de apertura `<body>`, agrega esto:

```erb
<html>
  <!-- ... -->
  <body>
    <div class="notice"><%= flash[:notice] %></div>
    <div class="alert"><%= flash[:alert] %></div>

    <%= yield %>
  </body>
</html>
```

Vamos a entender qué hace cada línea:

**`<div class="notice"><%= flash[:notice] %></div>`**
- Crea un div (una caja) con la clase CSS "notice"
- `<%= flash[:notice] %>` muestra el contenido del mensaje tipo notice (si existe)
- Si no hay mensaje, simplemente no muestra nada

**`<div class="alert"><%= flash[:alert] %></div>`**
- Lo mismo, pero para mensajes de tipo alert (advertencias)

💡 **¿Por qué ponemos ambos?** Porque diferentes acciones pueden crear diferentes tipos de mensajes. Cuando creas un producto, usas `notice` (positivo). Pero cuando eliminas algo o hay un error, podrías usar `alert` (advertencia). Al poner ambos en el layout, estamos preparados para cualquier situación.

#### ¡Veamos el Resultado! 🎉

Ahora, cuando crees un producto:

1. El controller lo guarda en la base de datos ✅
2. Establece el mensaje flash "¡Producto creado exitosamente!" 💬
3. Redirige a la página del producto 🔀
4. El layout detecta el flash y lo muestra en un div con clase "notice" 📺
5. ¡El usuario ve su mensaje de confirmación! 😊
6. Si recarga la página, el mensaje desaparece (ya cumplió su propósito) 👋

Tu aplicación ahora se siente más profesional y le habla al usuario. Es como agregar buenos modales - pequeños detalles que hacen una gran diferencia. ✨

💡 **¿Quieres profundizar más sobre el Flash?** Puedes aprender más sobre todas sus funcionalidades en la [Descripción General de Action Controller](https://guides.rubyonrails.org/action_controller_overview.html#the-flash). Pero por ahora, ¡ya sabes lo esencial para crear aplicaciones que se comunican con sus usuarios!

### ✏️ Editando Products (¡La Letra U de CRUD!)

Ya podemos crear productos, ¡excelente! Pero ¿qué pasa si cometimos un error en el nombre y queremos corregirlo? Ahí es donde entra la **U** de CRUD (Update - Actualizar).

El proceso de editar es MUY similar a crear. Fíjate en el patrón:

**Para Crear:**
- `new` → Muestra el formulario vacío
- `create` → Guarda el nuevo producto

**Para Editar:**
- `edit` → Muestra el formulario con los datos actuales del producto
- `update` → Guarda los cambios en el producto existente

¡Es como un espejo! 🪞 Vamos a implementar estas actions en el controller:

```ruby#23-34
class ProductsController < ApplicationController
  def index
    @products = Product.all
  end

  def show
    @product = Product.find(params[:id])
  end

  def new
    @product = Product.new
  end

  def create
    @product = Product.new(product_params)
    if @product.save
      redirect_to @product, notice: "Product created successfully!"
    else
      render :new, status: :unprocessable_entity
    end
  end

  def edit
    @product = Product.find(params[:id])
  end

  def update
    @product = Product.find(params[:id])
    if @product.update(product_params)
      redirect_to @product, notice: "Product updated successfully!"
    else
      render :edit, status: :unprocessable_entity
    end
  end

  private
    def product_params
      params.expect(product: [ :name ])
    end
end
```

¿Ves las similitudes? 🔍

**Action `edit`:**
- Busca el producto existente con `Product.find(params[:id])`
- Lo guarda en `@product`
- Rails automáticamente muestra `edit.html.erb`

**Action `update`:**
- Busca el producto con `Product.find(params[:id])`
- Intenta actualizarlo con `update(product_params)`
- Si funciona → redirige al producto
- Si falla → muestra el formulario de edit otra vez

¡Es casi idéntico a `new` y `create`, pero con productos que ya existen! 💡

#### ♻️ Extrayendo Partials (¡No Te Repitas!)

Espera un momento... Vamos a necesitar un formulario para `new.html.erb` Y otro para `edit.html.erb`. ¿Vamos a copiar y pegar el mismo código del formulario? 🤔

¡NO! ¿Recuerdas el principio DRY (Don't Repeat Yourself)? Rails tiene una solución perfecta: **Partials**.

Los Partials son como piezas de LEGO reutilizables. 🧱 Escribes el código una vez y lo usas en muchos lugares.

Vamos a mover el formulario a un archivo especial llamado `app/views/products/_form.html.erb`.

📌 **Dato importante:** Los archivos partial SIEMPRE empiezan con guion bajo (`_`) para que Rails sepa que es un partial y no una vista normal.

También vamos a hacer dos cambios importantes:
1. Cambiar `@product` por `product` (variable local, más flexible)
2. Agregar código para mostrar errores de validación

Crea el archivo `_form.html.erb` con este contenido:

```erb#1-4
<%= form_with model: product do |form| %>
  <% if form.object.errors.any? %>
    <p class="error"><%= form.object.errors.full_messages.first %></p>
  <% end %>

  <div>
    <%= form.label :name %>
    <%= form.text_field :name %>
  </div>

  <div>
    <%= form.submit %>
  </div>
<% end %>
```

Fíjate en las líneas que agregamos para mostrar errores:

```erb
<% if form.object.errors.any? %>
  <p class="error"><%= form.object.errors.full_messages.first %></p>
<% end %>
```

Esto dice: "Si hay algún error de validación, muéstralo en rojo". Así el usuario sabrá qué salió mal. 🚨

💡 **¿Por qué usar `product` en lugar de `@product`?**

Usar una variable local (sin `@`) hace que el partial sea más flexible. Puedes usarlo con cualquier producto que le pases, no solo con `@product`. Es como una función que acepta parámetros.

#### 🎯 Usando el Partial

Ahora que tenemos nuestro partial reutilizable, vamos a usarlo. Actualiza `app/views/products/new.html.erb` para que use el partial en lugar del formulario completo:

```erb#3
<h1>New product</h1>

<%= render "form", product: @product %>
<%= link_to "Cancel", products_path %>
```

Mira esa línea mágica: `<%= render "form", product: @product %>`

Se lee así:
- `render "form"` → "Renderiza el partial llamado `_form.html.erb`"
- `product: @product` → "Pásale la variable `@product` y llámala `product` dentro del partial"

¡Rails es tan inteligente que sabe buscar `_form.html.erb` aunque solo escribas "form"! 🧠

Ahora vamos a crear la vista de edit, que es casi idéntica gracias a nuestro partial reutilizable. Crea `app/views/products/edit.html.erb` con esto:

```erb#3
<h1>Edit product</h1>

<%= render "form", product: @product %>
<%= link_to "Cancel", @product %>
```

¿Ves? ¡Exactamente el mismo código! Solo cambiamos el título. El mismo partial funciona para crear Y para editar. ✨

**¡Eso es el poder de DRY!** Escribiste el formulario una vez y lo usas en dos lugares. Si algún día necesitas cambiar el formulario, solo lo editas en UN lugar (`_form.html.erb`) y automáticamente se actualiza en `new` y en `edit`. ¡Súper eficiente!

💡 **Para aprender más:** Consulta la [Guía de Action View](https://guides.rubyonrails.org/action_view_overview.html).

Ahora agreguemos un enlace "Edit" en la página de detalles del producto. Actualiza `app/views/products/show.html.erb`:

```erb#4
<h1><%= @product.name %></h1>

<%= link_to "Back", products_path %>
<%= link_to "Edit", edit_product_path(@product) %>
```

#### 🔄 Before Actions (¡Más Refactorización!)

Espera, tenemos otro caso de código repetido. 🔍 Fíjate:

- En `show` → `@product = Product.find(params[:id])`
- En `edit` → `@product = Product.find(params[:id])`
- En `update` → `@product = Product.find(params[:id])`

¡La misma línea tres veces! Eso va contra DRY. ¿Recuerdas? Don't Repeat Yourself.

Rails tiene una solución elegante: **Before Actions**. Es como decirle a Rails: "Antes de ejecutar estas actions, haz esto primero".

Imagina que es como cuando tu mamá te dice: "Antes de salir a jugar, haz tu tarea". El `before_action` es esa regla que se ejecuta automáticamente antes de ciertas actions. 📋

Vamos a crear un método privado llamado `set_product` que busca el producto, y le decimos a Rails que lo ejecute automáticamente antes de `show`, `edit` y `update`.

Mira cómo queda el controller refactorizado:

```ruby#2,8-9,24-25,27-33,36-38
class ProductsController < ApplicationController
  before_action :set_product, only: %i[ show edit update ]

  def index
    @products = Product.all
  end

  def show
  end

  def new
    @product = Product.new
  end

  def create
    @product = Product.new(product_params)
    if @product.save
      redirect_to @product, notice: "Product created successfully!"
    else
      render :new, status: :unprocessable_entity
    end
  end

  def edit
  end

  def update
    if @product.update(product_params)
      redirect_to @product, notice: "Product updated successfully!"
    else
      render :edit, status: :unprocessable_entity
    end
  end

  private
    def set_product
      @product = Product.find(params[:id])
    end

    def product_params
      params.expect(product: [ :name ])
    end
end
```

¿Ves la magia? ✨

**Línea 2:** `before_action :set_product, only: %i[ show edit update ]`

Esto dice: "Antes de ejecutar `show`, `edit` o `update`, llama primero al método `set_product`"

**Líneas 36-38:** El método privado `set_product`

Este método hace la búsqueda del producto. Como se ejecuta automáticamente antes de las actions que lo necesitan, podemos eliminar esa línea de `show`, `edit` y `update`.

**¡Resultado:** Código más limpio y organizado. Si algún día necesitas cambiar cómo buscas productos, solo lo cambias en UN lugar. 🎯

### 🗑️ Eliminando Products (¡La Letra D de CRUD!)

¡Última pieza del rompecabezas CRUD! La **D** de Delete (Eliminar). A veces necesitamos eliminar productos que ya no queremos en nuestra tienda.

Vamos a agregar la action `destroy` al controller para manejar peticiones `DELETE /products/:id`.

Como `destroy` también necesita buscar un producto existente (igual que `show`, `edit` y `update`), lo agregamos al `before_action`. ¡Así Rails automáticamente ejecuta `set_product` antes de `destroy` también!

```ruby#2,35-38
class ProductsController < ApplicationController
  before_action :set_product, only: %i[ show edit update destroy ]

  def index
    @products = Product.all
  end

  def show
  end

  def new
    @product = Product.new
  end

  def create
    @product = Product.new(product_params)
    if @product.save
      redirect_to @product, notice: "Product created successfully!"
    else
      render :new, status: :unprocessable_entity
    end
  end

  def edit
  end

  def update
    if @product.update(product_params)
      redirect_to @product, notice: "Product updated successfully!"
    else
      render :edit, status: :unprocessable_entity
    end
  end

  def destroy
    @product.destroy
    redirect_to products_path, notice: "Product deleted successfully!"
  end

  private
    def set_product
      @product = Product.find(params[:id])
    end

    def product_params
      params.expect(product: [ :name ])
    end
end
```

Mira la action `destroy`. ¡Súper simple! Solo dos líneas:

```ruby
def destroy
  @product.destroy
  redirect_to products_path
end
```

**1. `@product.destroy`** → Elimina el producto de la base de datos (gracias al `before_action`, `@product` ya está definido)

**2. `redirect_to products_path`** → Redirige al usuario a la lista de productos

¡Y ya! El producto desaparece de la base de datos. 💨

#### 🚨 Agregando el Botón Delete

Ahora necesitamos darle al usuario una forma de eliminar productos. Agreguemos un botón en la página de detalles. Actualiza `app/views/products/show.html.erb`:

```erb#5
<h1><%= @product.name %></h1>

<%= link_to "Back", products_path %>
<%= link_to "Edit", edit_product_path(@product) %>
<%= button_to "Delete", @product, method: :delete, data: { turbo_confirm: "Are you sure?" } %>
```

Aquí hay algo nuevo: **`button_to`**. Es diferente a `link_to`:

- **`link_to`** → Crea un enlace normal (`<a>`) para navegación
- **`button_to`** → Crea un formulario con un botón, perfecto para actions que cambian datos (como DELETE)

Fíjate en `data: { turbo_confirm: "Are you sure?" }`. Esto es seguridad extra. ⚠️

Cuando alguien presione "Delete", aparecerá una ventana emergente preguntando "Are you sure?" (¿Estás segura?). El usuario tiene que confirmar antes de que realmente se elimine el producto.

¡Es como cuando tu computadora te pregunta "¿Estás seguro de que quieres eliminar este archivo?" antes de moverlo a la basura! 🗑️

**¡Felicidades!** 🎉🎊 ¡Acabas de completar un CRUD completo! Ahora puedes:
- ✅ **C**reate (Crear productos)
- ✅ **R**ead (Ver lista y detalles)
- ✅ **U**pdate (Editar productos)
- ✅ **D**elete (Eliminar productos)

¡Eso es una aplicación web completamente funcional!

## 🔐 Agregando Autenticación (¡Seguridad Importante!)

Tenemos un pequeño problema de seguridad. 😱 En este momento, ¡CUALQUIER persona puede editar o eliminar productos! Imagina que alguien entra a tu tienda y empieza a cambiar precios o eliminar productos. ¡Sería un caos!

Necesitamos agregar **autenticación**. Autenticación significa verificar quién eres, como cuando muestras tu identificación o ingresas tu contraseña.

**La buena noticia:** ¡Rails hace esto súper fácil! Rails tiene un generador que crea todo un sistema de autenticación automáticamente. 🎁

Este generador va a crear:
- Un **modelo User** (para guardar usuarios en la base de datos)
- Un **modelo Session** (para recordar quién está conectado)
- Controllers y vistas para el inicio de sesión

Es como recibir un kit completo de seguridad. ¡Vamos a usarlo!

Regresa a tu terminal y ejecuta este comando mágico:

```bash
$ bin/rails generate authentication
```

¡Mira cuántos archivos creó! 📁 Rails generó todo un sistema de autenticación automáticamente. ¡Increíble!

Ahora necesitamos actualizar la base de datos para que tenga tablas para guardar usuarios. Ejecuta la migración:

```bash
$ bin/rails db:migrate
```

Este comando crea las tablas `users` y `sessions` en tu base de datos. ✨

### 👤 Creando Tu Primer Usuario

Ahora que tenemos las tablas listas, vamos a crear un usuario que pueda iniciar sesión. Para esto, abrimos la consola de Rails (¿la recuerdas? Es como tu laboratorio de experimentación):

```bash
$ bin/rails console
```

Una vez que la consola esté abierta, vamos a crear un usuario. Escribe este comando (puedes cambiar el email y la contraseña por los tuyos):

```irb
store(dev)> User.create! email_address: "you@example.org", password: "s3cr3t", password_confirmation: "s3cr3t"
```

¡Perfecto! 🎉 Acabas de crear tu primer usuario. Fíjate que pedimos la contraseña DOS veces (`password` y `password_confirmation`). Esto es una medida de seguridad común para asegurarte de que no cometiste un error al escribir tu contraseña.

### 🔄 Reiniciando el Servidor

El generador de autenticación agregó una gema especial llamada `bcrypt`. Esta gema es como una caja fuerte súper segura para las contraseñas. Convierte las contraseñas en códigos secretos que nadie puede leer (ni siquiera tú en la base de datos). ¡Eso es seguridad de nivel profesional! 🔒

Para que Rails cargue esta gema nueva, necesitas reiniciar el servidor. Si está corriendo, deténlo (presiona Ctrl+C) y vuelve a iniciarlo:

```bash
$ bin/rails server
```

### 🚪 Probando la Autenticación

¡Momento de la verdad! Ahora cuando visites cualquier página de tu aplicación, Rails te pedirá que inicies sesión.

Pruébalo visitando: https://TU-CODESPACE.github.dev/products/new

¿Ves? 🔐 Rails te pide email y contraseña. Ingresa los que usaste cuando creaste el usuario.

**Si los ingresas correctamente:**
- ✅ ¡Rails te dejará pasar!
- Tu navegador recordará que iniciaste sesión
- No tendrás que escribir tu contraseña en cada página (el navegador la guarda automáticamente)

**Si te equivocas:**
- ❌ Rails no te dejará entrar
- Puedes intentarlo de nuevo

¡Es como tener un guardia de seguridad en la puerta de tu aplicación! 💂


### 👋 Agregando Log Out (Cerrar Sesión)

Ya podemos iniciar sesión, ¡genial! Pero... ¿cómo cerramos sesión? Necesitamos un botón de "Log out".

Vamos a agregarlo en un lugar donde aparezca en TODAS las páginas. Para esto, editamos el **layout** principal de la aplicación.

**¿Qué es un layout?** 🤔 Es como la plantilla base de todas tus páginas. Todo lo que pongas en el layout aparecerá en cada página de tu aplicación. Es perfecto para cosas como menús de navegación o pies de página.

Abre `app/views/layouts/application.html.erb` y agrega una barra de navegación con un enlace a "Home" y un botón "Log out":

```erb#5-8,10,12
<!DOCTYPE html>
<html>
  <!-- ... -->
  <body>
    <nav>
      <%= link_to "Home", root_path %>
      <%= button_to "Log out", session_path, method: :delete if authenticated? %>
    </nav>

    <main>
      <div class="notice"><%= flash[:notice] %></div>
      <div class="alert"><%= flash[:alert] %></div>

      <%= yield %>
    </main>
  </body>
</html>
```

Mira esa línea del botón Log out:

```erb
<%= button_to "Log out", session_path, method: :delete if authenticated? %>
```

Tiene algo especial al final: `if authenticated?`. Esto dice: "Solo muestra este botón SI el usuario está autenticado (conectado)".

**¿Por qué?** Porque no tiene sentido mostrar un botón de "cerrar sesión" si nadie ha iniciado sesión, ¿verdad? 😄

Cuando alguien hace clic en "Log out", Rails:
1. Envía una petición DELETE a la ruta session
2. Elimina la sesión del usuario
3. El usuario queda desconectado

¡Es como salir de tu cuenta!

### 🌍 Permitiendo Acceso No Autenticado (Páginas Públicas)

Espera un momento... Tenemos un problema. 🤔

Por defecto, el generador de autenticación protege TODAS las páginas. Eso significa que alguien que visite tu tienda tiene que iniciar sesión solo para VER los productos.

Pero eso no tiene sentido, ¿verdad? Si tienes una tienda, quieres que la gente pueda ver tus productos sin necesidad de crear una cuenta primero. Solo deben iniciar sesión si quieren crear, editar o eliminar productos.

Entonces necesitamos decirle a Rails: "Oye, las páginas `index` y `show` son públicas. Cualquiera puede verlas sin iniciar sesión".

Abre `app/controllers/products_controller.rb` y agrega esta línea al principio:

```ruby#2
class ProductsController < ApplicationController
  allow_unauthenticated_access only: %i[ index show ]
  # ...
end
```

¡Perfecto! 🎉 Esa línea dice: "Permite acceso no autenticado SOLO en las actions `index` y `show`". Las demás actions (`new`, `create`, `edit`, `update`, `destroy`) siguen protegidas.

**Pruébalo:** Cierra sesión (haz clic en "Log out") y visita las páginas index y show de productos. ¡Verás que puedes acceder sin iniciar sesión! 👀

### 👁️ Mostrando Enlaces Solo para Usuarios Autenticados

Ahora que las páginas son públicas, tenemos que ser inteligentes con los enlaces que mostramos.

Piénsalo: Si alguien está visitando tu tienda sin iniciar sesión, no tiene sentido mostrarle un botón "New product" porque no podrá usarlo de todas formas.

Vamos a ocultar ciertos enlaces para usuarios no autenticados. Actualiza `app/views/products/index.html.erb`:

```erb
<%= link_to "New product", new_product_path if authenticated? %>
```

¿Ves el `if authenticated?` al final? Solo muestra el enlace "New product" si el usuario está conectado.

**Pruébalo:**
1. Cierra sesión (Log out) → El enlace "New product" desaparece ✨
2. Inicia sesión en https://TU-CODESPACE.github.dev/session/new → ¡El enlace aparece de nuevo!

#### 💡 Bonus: Agregar Enlace de Login

También puedes agregar un enlace "Login" en la barra de navegación que solo aparezca cuando el usuario NO esté conectado. Agrega esto en el layout:

```erb
<%= link_to "Login", new_session_path unless authenticated? %>
```

`unless authenticated?` es lo opuesto a `if authenticated?`. Dice: "Muestra esto A MENOS QUE el usuario esté autenticado".

#### 🔒 Protegiendo Más Enlaces

De la misma forma, actualiza `app/views/products/show.html.erb` para ocultar los enlaces "Edit" y "Delete" de los visitantes no autenticados:

```erb#4,7
<h1><%= @product.name %></h1>

<%= link_to "Back", products_path %>
<% if authenticated? %>
  <%= link_to "Edit", edit_product_path(@product) %>
  <%= button_to "Delete", @product, method: :delete, data: { turbo_confirm: "Are you sure?" } %>
<% end %>
```

## 📸 Carga de Archivos con Active Storage

¡Tu tienda necesita imágenes! ¿Qué es una tienda sin fotos de los productos? 🖼️

**Active Storage** es una característica increíble de Rails que hace que cargar archivos (como imágenes, PDFs, videos, etc.) sea súper fácil.

Imagina que Active Storage es como un asistente personal que:
- Guarda las imágenes que subes
- Las organiza automáticamente
- Las muestra cuando las necesitas

Vamos a agregar una imagen destacada (featured image) a nuestros productos. Primero, actualiza el modelo `Product`:

```ruby#2
class Product < ApplicationRecord
  has_one_attached :featured_image
  validates :name, presence: true
end
```

¡Esa línea es mágica! 🪄 `has_one_attached :featured_image` le dice a Rails: "Este producto puede tener UNA imagen adjunta llamada `featured_image`".

Rails hace todo el trabajo pesado automáticamente. No necesitas crear una tabla nueva ni nada complicado.

Ahora agreguemos un campo al formulario para que los usuarios puedan subir imágenes. Actualiza `app/views/products/_form.html.erb` y agrega esto antes del botón de envío:

```erb#4-7
<%= form_with model: product do |form| %>
  <%# ... %>

  <div>
    <%= form.label :featured_image, style: "display: block" %>
    <%= form.file_field :featured_image, accept: "image/*" %>
  </div>

  <div>
    <%= form.submit %>
  </div>
<% end %>
```

¡Perfecto! Ahora tu formulario tiene un botón "Choose File" (Elegir Archivo) para subir imágenes. 📤

El `accept: "image/*"` le dice al navegador: "Solo acepta archivos de imagen (jpg, png, gif, etc.)".

### 🔒 Permitiendo el Parámetro

¿Recuerdas Strong Parameters? Necesitamos decirle a Rails que está bien recibir el parámetro `featured_image` del formulario.

Actualiza `app/controllers/products_controller.rb` en el método `product_params`:

```ruby#3
    # Only allow a list of trusted parameters through.
    def product_params
      params.expect(product: [ :name, :description, :featured_image ])
    end
```

Agregamos `:featured_image` a la lista de parámetros permitidos. ✅

### 🖼️ Mostrando la Imagen

Por último, vamos a mostrar la imagen en la página de detalles del producto. Abre `app/views/products/show.html.erb` y agrega esto en la parte superior:

```erb
<%= image_tag @product.featured_image if @product.featured_image.attached? %>
```

**¿Qué hace esto?**
- `image_tag` → Helper de Rails que crea una etiqueta `<img>` HTML
- `if @product.featured_image.attached?` → Solo muestra la imagen SI hay una imagen adjunta (para no mostrar nada si el producto no tiene imagen)

### 🎉 ¡Pruébalo!

1. Ve a la página de editar un producto o crear uno nuevo
2. Haz clic en "Choose File" y selecciona una imagen de tu computadora
3. Guarda el producto
4. ¡Boom! 💥 La imagen aparece en la página de detalles del producto

**¡Increíble!** Rails manejó automáticamente:
- La subida del archivo
- Guardarla en el lugar correcto
- Mostrarla cuando la necesitas

✨ **Para aprender más:** Consulta la [Guía de Active Storage](https://guides.rubyonrails.org/active_storage_overview.html) para funciones avanzadas como redimensionar imágenes, subir videos, etc.

## 🎨 Agregando CSS (¡Dale Estilo a Tu Aplicación!)

Tu aplicación funciona perfectamente, ¡pero se ve un poco... aburrida! 😅 Es como una casa con todas las habitaciones listas pero sin pintar ni decorar.

**CSS** (Cascading Style Sheets - Hojas de Estilo en Cascada) es el lenguaje que usa para darle estilo, color y diseño a las páginas web. Es como el decorador de interiores de tu aplicación. 🎨

### 📦 Propshaft: El Organizador de Assets

Rails tiene un sistema llamado **Propshaft** que organiza todos tus archivos de CSS, JavaScript, imágenes y otros "assets" (recursos).

Piensa en Propshaft como un asistente súper organizado que:
- Toma todos tus archivos de CSS y JavaScript
- Los prepara y optimiza
- Los sirve al navegador de forma eficiente
- En producción, hasta los guarda en caché para que tu aplicación sea más rápida ⚡

No necesitas preocuparte mucho por cómo funciona Propshaft, ¡simplemente hace su trabajo en segundo plano!

✨ **Para aprender más:** Consulta la [Guía del Asset Pipeline](https://guides.rubyonrails.org/asset_pipeline.html).

### ✏️ Agregando Estilos

Vamos a darle un poco de estilo a nuestra tienda. Abre `app/assets/stylesheets/application.css` y agrega este CSS:

```css
body {
  font-family: Arial, Helvetica, sans-serif;
  padding: 1rem;
}

nav {
  justify-content: flex-end;
  display: flex;
  font-size: 0.875em;
  gap: 0.5rem;
  max-width: 1024px;
  margin: 0 auto;
  padding: 1rem;
}

nav a {
  display: inline-block;
}

main {
  max-width: 1024px;
  margin: 0 auto;
}

.alert,
.error {
  color: red;
}

.notice {
  color: green;
}

section.product {
  display: flex;
  gap: 1rem;
  flex-direction: row;
}

section.product img {
  border-radius: 8px;
  flex-basis: 50%;
  max-width: 50%;
}
```

¡Este CSS hace que tu aplicación se vea mucho mejor! 🎉

**¿Qué hacen estos estilos?**
- `body` → Establece la fuente y agrega un poco de espacio alrededor
- `nav` → Hace que la barra de navegación se vea ordenada
- `main` → Centra el contenido principal
- `.alert`, `.error`, `.notice` → Da colores a los mensajes (rojo para errores, verde para éxitos)
- `section.product` → Organiza la página de producto con la imagen al lado de la información

Ahora actualiza `app/views/products/show.html.erb` para usar estos nuevos estilos:

```erb#1,3,6,18-19
<p><%= link_to "Back", products_path %></p>

<section class="product">
  <%= image_tag @product.featured_image if @product.featured_image.attached? %>

  <section class="product-info">
    <h1><%= @product.name %></h1>
    <%= @product.description %>

    <% if authenticated? %>
      <%= link_to "Edit", edit_product_path(@product) %>
      <%= button_to "Delete", @product, method: :delete, data: { turbo_confirm: "Are you sure?" } %>
    <% end %>
  </section>
</section>
```

¡Recarga tu página en el navegador! 🔄 ¿Ves la diferencia? Tu aplicación ahora se ve mucho más profesional y organizada. La imagen del producto aparece al lado de la información, todo está bien alineado y los colores hacen que sea más fácil de leer.

**¡Felicidades!** Ahora tienes una aplicación con estilo. 🎨✨

---

## 🎊 ¿Qué Sigue? (¡Esto Es Solo El Comienzo!)

**¡FELICITACIONES!** 🎉🎉🎉

¡Acabas de construir tu primera aplicación Rails completa! Mira todo lo que has logrado:

✅ Creaste una aplicación Rails desde cero
✅ Entendiste MVC (Model-View-Controller)
✅ Trabajaste con bases de datos y migraciones
✅ Implementaste un CRUD completo (Create, Read, Update, Delete)
✅ Agregaste validaciones para proteger tus datos
✅ Creaste formularios interactivos
✅ Implementaste autenticación de usuarios
✅ Subiste archivos con Active Storage
✅ Diseñaste tu aplicación con CSS

**¡Eso es INCREÍBLE!** 💪 Muchos adultos no saben hacer todo esto. Deberías estar súper orgullosa de ti misma.

### 🚀 Próximos Pasos

¿Quieres seguir aprendiendo? Aquí tienes algunas ideas:

**1. Continúa con la guía completa:**
- [Getting Started with Rails (Guía Completa)](https://guides.rubyonrails.org/getting_started.html) - Profundiza más en Rails

**2. Explora temas específicos:**
- [Fundamentos de Active Record](https://guides.rubyonrails.org/active_record_basics.html) - Aprende más sobre modelos y bases de datos
- [Layouts y Renderizado](https://guides.rubyonrails.org/layouts_and_rendering.html) - Mejora tus vistas
- [Testing de Aplicaciones Rails](https://guides.rubyonrails.org/testing.html) - Aprende a probar tu código
- [Depurando Aplicaciones Rails](https://guides.rubyonrails.org/debugging_rails_applications.html) - Encuentra y arregla errores como una pro

**3. Mejora tu aplicación:**
- Agrega más campos a Product (precio, descripción, categoría)
- Crea un carrito de compras
- Agrega comentarios o reseñas de productos
- Mejora el diseño con más CSS o usa frameworks como Tailwind o Bootstrap

### 💡 Recuerda

La programación es como aprender un instrumento musical o un nuevo idioma. Al principio puede parecer difícil, pero con práctica se vuelve cada vez más natural.

**¡Sigue construyendo, sigue aprendiendo y sigue siendo curiosa!** 🌟

Cada programadora exitosa comenzó exactamente donde estás tú ahora. El único secreto es: nunca dejar de aprender.

**¡Adelante, programadora!** 👩‍💻✨
