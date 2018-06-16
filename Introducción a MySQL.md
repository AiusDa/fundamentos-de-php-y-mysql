# Introducción a MySQL

## Fundamentos

### Conexión a MySQL desde terminal

Para conectarse a una base de datos se requiere escribir el siguiente comando:

    > mysql -u root -p

Donde:

- mysql es la ejecución del programa
- -u {user} se indica el usuario con el que se va a conectar (en el ejemplo se está usando **root**)
- -p indica que se le pasará la contraseña

Posteriormente esperará a que se escriba la contraseña seguida de un intro.

A partir de este momento podremos empezar a trabajar con las bases de datos en MySQL.

NOTA: Según el usuario y sus permisos se podrán realizar unas u otras acciones, en nuestros ejemplos supondremos que se estará trabajando todo el tiempo con el usuario root, mismo que desde la instalación de MySQL cuenta con todos los permisos.

## Estados básicos

Todos los estados en MySQL deberán ser finalizados con un ";" (punto y coma), en caso contrario al darle intro no ejecutará dicho comando.

### SHOW

Podemos usar el comando para mostrar las bases de datos o tablas:

	> SHOW DATABASES;
	...
	> SHOW TABLES; // Habiendo seleccionado previamente una base de datos
	...

### CREATE  DATABASE

	CREATE DATABASE <database_name>;

Crea una Base de Datos.

### DROP  DATABASE

	DROP DATABASE <database_name>;

Elimina una Base de Datos.

### CREATE  TABLE

	CREATE TABLE <database>.<table> (
		column1 datatype,
		column2 datatype,
		...
	);
	CREATE TABLE <table> (
		column1 datatype,
		column2 datatype,
		...
	); // Si se seleccionado una base de datos previamente

Crea una tabla y declara sus campos.

### DROP TABLE

	DROP TABLE <database>.<table>;
	DROP TABLE <table>; // Si se ha seleccionado previamente una base de datos

Elimina una tabla.

### TRUNCATE TABLE

	TRUNCATE TABLE <database>.<table>;
	TRUNCATE TABLE <table>; // Si se ha seleccionado previamente una base de datos

Elimina todos los datos de una tabla sin eliminarla

### ALTER TABLE

	ALTER TABLE <database>.<table>
	ADD <column_name> <datatype>;
	ALTER TABLE <table>
	DROP COLUMN <column_name>; // Si se ha seleccionado previamente una base de datos

Usado para agregar, eliminar o modificar columnas.

### USE

	use <database>;

Muestra la lista de bases de datos.

### SELECT FROM

    SELECT * FROM <database>.<table>;
    SELECT * FROM <table>; // Si se ha seleccionado previamente una base de datos

Muestra los datos de la tabla indicada, el "*" (asterisco) indica que se muestren todos los campos existentes, este valor puede ser sustituido por una lista de campos previamente declarados en la tabla:

	SELECT <field1>, <field2>, ..., <fieldn> FROM <table>

### SELECT FROM WHERE

    SELECT * FROM <database>.<table> WHERE condition;
    SELECT * FROM <table> WHERE condition; // Si se ha seleccionado previamente una base de datos

Filtra los resultados que coinciden con la condición dada.

### INSERT INTO

	> INSERT INTO <database>.<table> (column1, column2, column3, ...)
	VALUES (value1, value2, value3, ...);

	> INSERT INTO <table> (column1, column2, column3, ...)
	VALUES (value1, value2, value3, ...); // Si se ha seleccionado previamente una base de datos

	INSERT INTO <table>
	VALUES (value1, value2, value3, ...); // Si se ha seleccionado previamente una base de datos, se deben llenar todos los campos y asegurar que se coloquen en orden en el que aparecen en la tabla

Inserta un registro en la tabla.

### UPDATE SET

	UPDATE <database>.<table>
	SET column1 = value1, column2 = value2;
	UPDATE <table>
	SET column1 = value1, column2 = value2; // Si se ha seleccionado previamente una base de datos

Actualiza los valores de los campos señalados de una tabla.

### DELETE

	DELETE FROM <database>.<table>;
	DELETE FROM <table>; // Si se ha seleccionado previamente una base de datos

Elimina los registros de una tabla.

NOTA: Es importante agregarle siempre un WHERE a DELETE para que sólo se eliminen los registros bajo una condición dada.

## Tipos de de campos

| Tipo de dato | Descripción | Valores que toma |
|--|--|--|
| CHAR(n) | Almacena cadenas de caracteres con una longitud máxima fija de 255 caracteres. Dentro de ella, n indica la longitud del campo, esto es, la cantida |  |
| DATE |  |  |
| DECIMAL(m,n) |  |  |
| FLOAT(m,n) |  |  |
| INTEGER(n) |  |  |
| TEXT |  |  |
| TIMESTAMP |  |  |
| VARCHAR(n) |  |  |
| YEAR |  |  |

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTczODI5MTMyOCw2NDA2NzQ4NzhdfQ==
-->