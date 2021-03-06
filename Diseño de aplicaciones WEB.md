# 4. Diseño de aplicaciones WEB

## 4.1 Conceptos generales

### 4.2 Importando archivos externos

Para contar con un código más limpio y escalable podemos hacer módulos como en otros lenguajes, la diferencia está en la forma en que PHP lo hace; para esto cuenta con dos sentencias:

- [require](http://php.net/manual/es/function.require.php)
- [include](http://php.net/manual/es/function.include.php)

Ambas sirven para poder importar código contenido en otro archivo, sin embargo su diferencia es que Requiere genera un error fatal si es que algo falla deteniendo el script, en cambio Include sólo genera una advertencia y se puede continuar trabajando.

Adicionalmente tanto Require como Include tienen una forma opcional de trabajarse, esta permite garantizar que sólo una vez se ha hecho la importación del archivo, si previamente se ha hecho no lo incluye sin generar error, estas sentencias son:

- require_once
- include_once

### 4.3 Métodos de envío de formularios (GET y POST)

Quizá los dos métodos (o verbos) más famosos del http son **GET** y **POST**, históricamente estos métodos se han utilizado para manejar información de formularios, aunque a veces con el concepto equivocado.

GET se ha considerado como el método a utilizar cuando no necesitas transportar información segura, al contrario, POST se ha usado para trabajar con información que no se quiere revelar ya que es sensible.

En realidad en una aplicación RESTFul, el verbo GET es usado para obtener datos únicamente, pasando por query params la especificación de la información que quiere obtenerse. El verbo POST es usado para crear nuevos elementos dentro de nuestra aplicación.

PHP cuenta con dos varibales globales para manejar estos métodos:

- [$_GET](http://php.net/manual/es/reserved.variables.get.php)
- [$_POST](http://php.net/manual/es/reserved.variables.post.php)

Dichas variables son arrays asociativos que varían según la información dada.

### 4.4 Archivos enviados a servidor desde formulario

Una característica con la que ya viene incluido PHP es el poder manejar archivos enviados desde formulario, para esto se usa la variable global [$_FILES](http://php.net/manual/es/reserved.variables.files.php).

Al igual que $_GET o $_POST, $_FILES es un array asociativo, sin embargo por default este por cada elemento arroja más información que un string:

- name: nombre del archivo importado
- type: tipo del archivo
- tmp_name: nombre temporal asignado por el sistema
- error: error de subida si es que hubo uno
- size: tamaño en bytes del archivo

## 4.2 Buenas prácticas de arquitectura

### 4.2.1 Modelo MVC

Quizá este tipo de modelado sea uno de los más famoso, aunque en la actualidad se han extendido muchos más y quizá ofrezcan una mejor arquitectura, la verdad es que este es aún muy utilizado en la mayoría de **Frameworks** de PHP.

Este modelo consiste en separar el código en tres bloques diferentes:

- Modelo: Representación de la información con la cual se operará
- Vista: La interfaz con la que el usuario va a interactuar (UI)
- Controlador: Contiene la lógica con la que se puede operar los datos previamente a mostrarse en la vista

### 4.2.2 Modularización

Es bueno mantener componentes con funciones específicas, esto con el fin de poder reutilizarlos o modificarlos de forma más sencilla.

Uno de los ejemplos más sencillos pero útiles es el de tener un archivo util.php o helper.php que contengan una serie de funciones que se pueden utilizar en cualquier parte del código independientemente de la función que tenga cada módulo. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzU3MjM0Njg5LC0yOTU4MjM4ODgsLTE5Nz
QyNDU1NTEsLTEzNDkyMzg0MTksLTM0NDc3NDI0OV19
-->