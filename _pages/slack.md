---
layout: inner
title: Railslack
lead_text: Crea un clon de Slack desde cero
permalink: /railslack/
---

<div class="repo">
  <h3>Repostitorio de la aplicación</h3>
  <a href="https://github.com/railsgirls-cali/example-railslack">
    https://github.com/railsgirls-cali/example-railslack</a>
</div>

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

**NOTA** Si estás usando c9 no vas a poder acceder a la página de inicio usando la URL anterior, necesitas una URL especial, para el caso del taller la URL será genrada de la siguiente forma:

http://railslack-**your_id**-railsgirlscali.c9users.io/
