---


---

<h1 id="introducción-al-lenguaje-php">2. Introducción al lenguaje PHP</h1>
<h2 id="sintaxis-básica-y-buenas-prácticas"><a href="http://php.net/manual/es/language.basic-syntax.phpmode.php">Sintaxis básica y buenas prácticas</a></h2>
<p>El intérprete de PHP normalmente se encuentra configurado para leer la información contenido en archivos con extensión .php, aunque en algunas aplicaciones o frameworks suelen configurar también la extensión .phtml para diferenciar los archivos que sólo contendrán código de PHP (.php) y los que tendrán código de PHP y HTML (.phtml), siendo que este último tipo de archivos no es parte del estándar.</p>
<p>Para indicarle al intérprete de PHP cuando debe leer un código que no es HTML se encierra dicho código entre <strong>&lt;?php ?&gt;</strong> o <strong>&lt;?=  ?&gt;</strong>, a pesar de que existen otras formas de que también se pueda indicar un código PHP (que no son parte del estándar), estas son las formas recomendadas por el estándar PSR-1.</p>
<p>Ejemplo:</p>
<pre><code>&lt;?php
    echo "Hola Mundo";
?&gt;
</code></pre>
<p>El código anterior lo que mostraría sería “Hola Mundo” únicamente. Hay que poner especial atención en que cada sentencia de código debe finalizar con “;”.</p>
<p>Como buenas prácticas para escribir código y respetar los <a href="https://www.php-fig.org/psr/">PSR</a> podemos destacan las siguientes reglas:</p>
<ul>
<li>La identación debe usar cuatro espacios (no usar tabs)</li>
<li>Crear comentarios suficientemente descriptivos</li>
<li>Los archivos deben usar encodeo <strong>UTF-8</strong> sin BOM</li>
<li>La etiqueta de cierre “?&gt;” no debe colocare en archivos que sólo tengan código PHP</li>
<li>Todos los archivos deben terminar con una línea en blanco</li>
</ul>
<p>Más adelante conforme vayamos presentando más sobre la estructura de archivos PHP se irán indicando otras importantes reglas sintácticas.</p>
<h2 id="variables"><a href="http://php.net/manual/es/language.variables.php">Variables</a></h2>
<p>Las variables se definen formalmente como espacios de memoria que almacenan algún dato, es decir, son como contenedores en los que iremos guardando información a lo largo del ciclo de vida del programa y que posteriormente iremos llenando con nueva información o leyéndola para hacer algún cálculo o mostrar dicha información.</p>
<h3 id="nombre-de-variables">Nombre de variables</h3>
<p>Las variables se de identifican porque siempre empiezan con el signo “<span class="katex--inline">KaTeX parse error: Expected group after '_' at position 80: … regex "[a-zA-Z_̲\x7f-\xff][a-zA…</span>” y precedido por cualquiera de los bytes del 127 al 255 (<em>0x7f-0xff</em>).</p>
<pre><code>// Nombres válidos de variables
$miVar // Válido, comienza con una letra
$MiVar // Válido, comienza con una letra
$_miVar1 // Válido comienza con un guión bajo

1mivar // Inválido no comienza con el signo de $
$1mivar // Inválido comienza con un número
</code></pre>
<h3 id="variables-predefinidas"><a href="http://php.net/manual/es/language.variables.predefined.php">Variables predefinidas</a></h3>
<p>Existe un grupo de nombres de variables predefinido que sólo pueden ser leído su valor pero no reescrito:</p>
<ul>
<li><a href="http://php.net/manual/es/reserved.variables.globals.php">$GLOBALS</a></li>
<li><a href="http://php.net/manual/es/reserved.variables.server.php">$_SERVER</a></li>
<li><a href="http://php.net/manual/es/reserved.variables.get.php">$_GET</a></li>
<li><a href="http://php.net/manual/es/reserved.variables.post.php">$_POST</a></li>
<li><a href="http://php.net/manual/es/reserved.variables.files.php">$_FILES</a></li>
<li><a href="http://php.net/manual/es/reserved.variables.cookies.php">$_COOKIE</a></li>
<li><a href="http://php.net/manual/es/reserved.variables.session.php">$_SESSION</a></li>
<li><a href="http://php.net/manual/es/reserved.variables.request.php">$_REQUEST</a></li>
<li><a href="http://php.net/manual/es/reserved.variables.environment.php">$_ENV</a></li>
</ul>
<h3 id="asignación-de-valores">Asignación de valores</h3>
<p>Para que nuestra variable pueda almacenar un valor se usa el operador “=” (igual), más adelante ahondaremos más sobre este y otros operadores.</p>
<p>Ejemplo:</p>
<pre><code>$counter = 0;
$message = "Hola mundo";
</code></pre>
<p>PHP es un <strong>lenguaje dinámicamente tipado</strong>, es decir, cuando declaras una variable no necesitas indicar qué tipo de dato contendrá (más adelante veremos los tipos de datos existentes en PHP) como otros lenguajes como <strong>Java</strong> o <strong>C#</strong>, ya que al asignarle un valor el <strong>intérprete infiere el tipo de la variable</strong>.</p>
<p>Esto permite que a la misma variable pueda asignarle varios datos de diferentes tipos sin problema alguno;</p>
<p>Ejemplo:</p>
<pre><code>$a = "Hola!";
$a = 1;
</code></pre>
<h3 id="ámbito-de-las-variables"><a href="http://php.net/manual/es/language.variables.scope.php">Ámbito de las variables</a></h3>
<p>Con ámbito de las variables nos referimos al espacio en el que una variable existe; hay dos tipos de ámbitos: <strong>global</strong> y <strong>local</strong>.</p>
<p>Las <strong>variables globales</strong> son aquellas que están disponibles desde cualquier parte del código, estas fueron creadas fuera de cualquier función.</p>
<p>Las <strong>variables locales</strong> son todas aquellas que fueron declaradas dentro de una función, por lo que su validez es sólo dentro de ella y fuera no puede ser utilizada.</p>
<p>Ejemplo:</p>
<pre><code>&lt;?php
$a = "Variable global\n";
$b = "Otra variable global\n";
function myFunction()
{
    global $a;
    echo $a; // Regresa "Variable global"
    echo $b; // Regresar un error
    $c = "Variable local";
}
myFunction();
echo $c; // Regresa Error
</code></pre>
<h2 id="constantes"><a href="http://php.net/manual/es/language.constants.php">Constantes</a></h2>
<p>Al igual que las variables, las constantes son espacios de memoria que pueden almacenar cualquier tipo de dato, sin embargo estas tienen la restricción de que no es posible cambiar su información una vez que se le asignó.</p>
<p>Las constantes pueden ser definidas y accedidas desde cualquier sitio sin importar las reglas de acceso de variables.</p>
<p>Para declarar una constante existen dos formas:</p>
<p>Usando la palabra reservada const:</p>
<pre><code>const PI = 3.1416;
</code></pre>
<p>Usando la función <strong>define(name, value)</strong>, donde:</p>
<ul>
<li>name: Es el nombre de la constante y que debe cumplir con las mismas especificaciones que los nombres de variables, salvo que este no está precedido por un signo de “$” y por convención debe escribirse siempre en mayúsculas y con “_” (guión bajo) para separar palabras</li>
<li>value: Es cualquier valor que se le asignará a la constante</li>
</ul>
<p>La principal diferencia es que define en tiempo de ejecución</p>
<p>Ejemplo:</p>
<pre><code>define("CONSTANTE", "12345") // Válido ya que empieza con una letra
define("MI_CONSTANTE", "Esta es mi constante"); // Válido ya que empieza con una letra
define("1_CONSTANTE", "Nombre incorrecto"); // Inválido ya que empieza con un número
define("__CONSTANTE__", "No recomendado") // Válido pero no recomendado
</code></pre>
<p>Las constantes desde su definición se crean siempre con un ámbito global.</p>
<h3 id="constantes-predefinidas-del-núcleo"><a href="http://php.net/manual/es/reserved.constants.php">Constantes predefinidas del núcleo</a></h3>
<p>PHP cuenta con constantes que se encuentran disponibles desde su instalación, por lo que los nombres se encuentran reservados y no podemos utilizarlos para definir valores propios. Entre ella encontramos las siguientes:</p>

<table>
<thead>
<tr>
<th>Constante</th>
<th>Descripción</th>
</tr>
</thead>
<tbody>
<tr>
<td>PHP_VERSION</td>
<td>La versión actual de PHP en notación “mayor.menor.edición[extra]”.</td>
</tr>
<tr>
<td>PHP_INT_MAX</td>
<td>El número entero más grande admitido en esta compilación de PHP</td>
</tr>
<tr>
<td>PHP_INT_MIM</td>
<td>El número entero más pequeño admitido en esta compilación de PHP</td>
</tr>
<tr>
<td>PHP_FLOAT_MIN</td>
<td>El menor número de punto flotante representable</td>
</tr>
<tr>
<td>PHP_FLOAT_MAX</td>
<td>El mayor número de punto flotante representable</td>
</tr>
<tr>
<td>TRUE</td>
<td>Representa una variable con valor verdadero</td>
</tr>
<tr>
<td>FALSE</td>
<td>Representa una variable con valor falso</td>
</tr>
<tr>
<td>NULL</td>
<td>Representa una variable sin valor</td>
</tr>
</tbody>
</table><h3 id="constantes-mágicas"><a href="http://php.net/manual/es/language.constants.predefined.php">Constantes mágicas</a></h3>
<p>Son nueve constantes que cambian según el contexto en el que se usan</p>

<table>
<thead>
<tr>
<th>Constante</th>
<th>Descripción</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>__LINE__</code></td>
<td>El número de línea actual en el fichero.</td>
</tr>
<tr>
<td><code>__FILE__</code></td>
<td>Ruta completa y nombre del fichero con enlaces simbólicos resueltos. Si se usa dentro de un include, devolverá el nombre del fichero incluido.</td>
</tr>
<tr>
<td><code>__DIR__</code></td>
<td>Directorio del fichero. Si se utiliza dentro de un include, devolverá el directorio del fichero incluído. Esta constante es igual que <em>dirname(<code>__FILE__</code>)</em>. El nombre del directorio no lleva la barra final a no ser que esté en el directorio root.</td>
</tr>
<tr>
<td><code>__FUNCTION__</code></td>
<td>Nombre de la función.</td>
</tr>
<tr>
<td><code>__CLASS__</code></td>
<td>Nombre de la clase. El nombre de la clase incluye el namespace declarado en (p.e.j. <em>Foo\Bar</em>). Tenga en cuenta que a partir de PHP 5.4 <code>__CLASS__</code> también funciona con traits. Cuando es usado en un método trait, <code>__CLASS__</code> es el nombre de la clase del trait que está siendo utilizado.</td>
</tr>
<tr>
<td><code>__TRAIT__</code></td>
<td>El nombre del trait. El nombre del trait incluye el espacio de nombres en el que fue declarado (p.e.j. <code>_Foo\Bar_</code>).</td>
</tr>
<tr>
<td><code>__METHOD__</code></td>
<td>Nombre del método de la clase.</td>
</tr>
<tr>
<td><code>__NAMESPACE__</code></td>
<td>Nombre del espacio de nombres actual.</td>
</tr>
<tr>
<td><code>ClassName::class</code></td>
<td>El nombre de clase completamente cualificado.</td>
</tr>
</tbody>
</table><h2 id="comentarios"><a href="http://php.net/manual/es/language.basic-syntax.comments.php">Comentarios</a></h2>
<p>Los comentarios son una parte fundamental en cualquier lenguaje de programación, aunque en la ejecución no aportan nada, son una excelente herramienta para mantener un código bien documentado.</p>
<p>En PHP hay tres formas de hacer comentarios:</p>
<pre><code>// Comentario de una sóla línea
# Comentario al estilo de  consola de una línea
/* Comentario de
 * varias líneas
 */
</code></pre>
<h2 id="tipos-de-datos"><a href="http://php.net/manual/es/language.types.php">Tipos de datos</a></h2>
<p>Tipo se le dice a un espacio de memoria que cuenta con cierta longitud de información, en PHP se dividen de la siguiente forma:</p>
<h3 id="escalares">Escalares</h3>
<h4 id="string"><a href="http://php.net/manual/es/language.types.string.php">string</a></h4>
<p>Los string o cadenas de caracteres, son uno de los tipos de datos más usados, su sintaxis puede ser de tres formas formas:</p>
<pre><code>// String con Comillas dobles
$comillasDobles = "Comillas dobles";
// String con Comillas simples
$comillasSimples = 'Comillas simples';
// String con Heredoc
$heredoc = &lt;&lt;&lt;&lt;EOD
Ejemplon con
más de una línea
EOD;
</code></pre>
<p>La principal diferencia está en que las comillas dobles permiten <strong>interpolar</strong> variables, es decir si colocamos una variable dentro de las comillas dobles el valor almacenado en dicha variable será interpretado antes de mostrarse:</p>
<pre><code>$nombre = "Juan";
echo "Hola $nombre"; // Muestra "Hola Juan"
</code></pre>
<p>Si quisiéramos hacer algo parecido al ejemplo anterior con comillas simples tendríamos que hacer uso de la <strong>concatenación</strong>:</p>
<pre><code>$nombre = "Pedro";
echo "Hola " . $nombre; // Muestra "Hola Pedro"
</code></pre>
<p>La concatenación también es posible con las comillas simples, sin embargo es más semántico el uso de la interpolación cuando se usa esta sintaxis.</p>
<p>PHP cuenta con varias funciones para tratar a las cadenas de caracteres, entre ellas encontramos:</p>
<ul>
<li><a href="http://php.net/manual/es/function.crypt.php">crypt</a>  — Hash de cadenas de un sólo sentido</li>
<li><a href="http://php.net/manual/es/function.echo.php">echo</a>  — Muestra una o más cadenas</li>
<li><a href="http://php.net/manual/es/function.explode.php">explode</a>  — Divide un string en varios string</li>
<li><a href="http://php.net/manual/es/function.implode.php">implode</a>  — Une elementos de un array en un string</li>
<li><a href="http://php.net/manual/es/function.md5.php">md5</a>  — Calcula el ‘hash’ md5 de un string</li>
<li><a href="http://php.net/manual/es/function.printf.php">printf</a>  — Imprimir una cadena con formato</li>
<li><a href="http://php.net/manual/es/function.strlen.php">strlen</a>  — Obtiene la longitud de un string</li>
<li><a href="http://php.net/manual/es/function.trim.php">trim</a>  — Elimina espacio en blanco (u otro tipo de caracteres) del inicio y el final de la cadena</li>
<li><a href="http://php.net/manual/es/function.wordwrap.php">wordwrap</a>  — Ajusta un string hasta un número dado de caracteres</li>
</ul>
<h4 id="integer"><a href="http://php.net/manual/es/language.types.integer.php">integer</a></h4>
<p>Los integers o números enteros son un tipo primitivo, el número máximo que puede almacenar normalmente es de 2147483647, si llegara a necesitarse un número mayor, tendría que hacerse uso de un float.</p>
<h4 id="float"><a href="http://php.net/manual/es/language.types.float.php">float</a></h4>
<p>Así como los integer, los float son uno de los tipos usados para almacenar números, sin embargo este permite números con parte decimal y el número máximo es bastante superior siendo normalmente de ~1.8e308.</p>
<h4 id="boolean"><a href="http://php.net/manual/es/language.types.boolean.php">boolean</a></h4>
<p>Los boolean son un tipo bastante especial, ya que sólo almacenan dos posibles valores, true (verdadero) o false (falso), su uso es bastante extendido principalmente en la toma de decisiones como en las estructuras de control.</p>
<h3 id="compuestos">Compuestos</h3>
<h4 id="array"><a href="http://php.net/manual/es/language.types.array.php">array</a></h4>
<p>Existen dos tipos de arrays o arreglos (en algunos casos también llamados vectores):</p>
<pre><code>// Indexados
$arrayIndexado = array("valor1", "valor2");
// Para acceder a uno de sus valores se hace a través de un índice entero, siendo el 0 el primero y el último es igual a la cantidad de valores - 1
echo $arrayIndexado[0]; # Muestra valor1
// Asociativos
$arrayAsociativo = array(
	"foo" =&gt; "valor1",
	"bar" =&gt; "valor2",
	100 =&gt; -100,
	-100 =&gt; 100,
);
// Para acceder a su valor se debe obtener pasando el nombre de la llave del elemento que se requiere obtener su valor
echo $arrayAsociativo["bar"]; # Muestra valor2
</code></pre>
<p>Así mismo también se les pueden catalogar como:</p>
<pre><code>// Unidimensionales (como los vistos ya anteriormente)
$arrayUnidimensional = [1, 2, 3, 4];
echo $arrayUnidimensional[2]; // Muestra el valor 3
// Multidimensionales	
$arrayMultidimensional = [
	[1, 2, 3, 4],
	[5, 6, 7, 8],
	[9, 10, 11, 12],
];
// Se accede colocando los índices del valor requerido, en este caso son dos, si usáramos sólo uno retornaría un array
echo $arrayMultidimensional[1][3]; // Muestra el valor 8
</code></pre>
<p>Los arrays multidimensionales pueden tener tantos niveles como se requiera.</p>
<h4 id="object"><a href="http://php.net/manual/es/language.types.object.php">object</a></h4>
<p>Los objetos son un tipo derivado de la programación orientada a objetos, en el cual tenemos que definir una clase y el objeto es una instancia (duplicado aislado) de dicha clase.</p>
<h4 id="callable"><a href="http://php.net/manual/es/language.types.callable.php">callable</a></h4>
<h4 id="iterable"><a href="http://php.net/manual/es/language.types.iterable.php">iterable</a></h4>
<h3 id="especiales">Especiales</h3>
<h4 id="resource"><a href="http://php.net/manual/es/language.types.resource.php">resource</a></h4>
<h4 id="null"><a href="http://php.net/manual/es/language.types.null.php">NULL</a></h4>
<h3 id="pseudotipos"><a href="http://php.net/manual/es/language.pseudo-types.php">Pseudotipos</a></h3>
<h4 id="mixed">mixed</h4>
<h4 id="number">number</h4>
<h4 id="callback">callback</h4>
<h4 id="arrayobject">array|object</h4>
<h4 id="void">void</h4>
<p>Y por último la pseudo variable <strong>$</strong>.</p>
<p>Para cada tipo existen operaciones especificas que nos ayudan a resolver problemas comunes, sin embargo, al ser una gran cantidad no veremos todas, e iremos revisando algunas más comunes conforme avancemos.</p>
<h2 id="operadores"><a href="http://php.net/manual/es/language.operators.php">Operadores</a></h2>
<h3 id="operadores-y-precedencia">Operadores y <a href="http://php.net/manual/es/language.operators.precedence.php">Precedencia</a></h3>
<p>La precedencia de operadores</p>

<table>
<thead>
<tr>
<th>Asociatividad</th>
<th>Operadores</th>
<th>Información adicional</th>
</tr>
</thead>
<tbody>
<tr>
<td>no asociativo</td>
<td><em>clone</em>  <em>new</em></td>
<td><a href="http://php.net/manual/es/language.oop5.cloning.php">clone</a> and <a href="http://php.net/manual/es/language.oop5.basic.php#language.oop5.basic.new">new</a></td>
</tr>
<tr>
<td>izquierda</td>
<td><em>[</em></td>
<td><a href="http://php.net/manual/es/function.array.php">array()</a></td>
</tr>
<tr>
<td>derecha</td>
<td><em>**</em></td>
<td><a href="http://php.net/manual/es/language.operators.arithmetic.php">aritmética</a></td>
</tr>
<tr>
<td>derecha</td>
<td><em>++</em>  <em>–</em>  <em>~</em>  <em>(int)</em>  <em>(float)</em>  <em>(string)</em>  <em>(array)</em>  <em>(object)</em>  <em>(bool)</em>  <em>@</em></td>
<td><a href="http://php.net/manual/es/language.types.php">tipos</a> e <a href="http://php.net/manual/es/language.operators.increment.php">incremento/decremento</a></td>
</tr>
<tr>
<td>no asociativo</td>
<td><em>instanceof</em></td>
<td><a href="http://php.net/manual/es/language.types.php">tipos</a></td>
</tr>
<tr>
<td>derecha</td>
<td><em>!</em></td>
<td><a href="http://php.net/manual/es/language.operators.logical.php">lógico</a></td>
</tr>
<tr>
<td>izquierda</td>
<td><em>*</em>  <em>/</em>  <em>%</em></td>
<td><a href="http://php.net/manual/es/language.operators.arithmetic.php">aritmética</a></td>
</tr>
<tr>
<td>izquierda</td>
<td><em>+</em>  <em>-</em>  <em>.</em></td>
<td><a href="http://php.net/manual/es/language.operators.arithmetic.php">aritmética</a>  y  <a href="http://php.net/manual/es/language.operators.string.php">string</a></td>
</tr>
<tr>
<td>izquierda</td>
<td><em>&lt;&lt;</em>  <em>&gt;&gt;</em></td>
<td><a href="http://php.net/manual/es/language.operators.bitwise.php">bit a bit</a></td>
</tr>
<tr>
<td>no asociativo</td>
<td><em>&lt;</em>  <em>&lt;=</em>  <em>&gt;</em>  <em>&gt;=</em></td>
<td><a href="http://php.net/manual/es/language.operators.comparison.php">comparación</a></td>
</tr>
<tr>
<td>no asociativo</td>
<td><em>==</em>  <em>!=</em>  <em>===</em>  <em>!==</em>  <em>&lt;&gt;</em>  <em>&lt;=&gt;</em></td>
<td><a href="http://php.net/manual/es/language.operators.comparison.php">comparación</a></td>
</tr>
<tr>
<td>izquierda</td>
<td><em>&amp;</em></td>
<td><a href="http://php.net/manual/es/language.operators.bitwise.php">bit a bit</a> y <a href="http://php.net/manual/es/language.references.php">referencias</a></td>
</tr>
<tr>
<td>izquierda</td>
<td><em>^</em></td>
<td><a href="http://php.net/manual/es/language.operators.bitwise.php">bit a bit</a></td>
</tr>
<tr>
<td>izquierda</td>
<td>_</td>
<td>_</td>
</tr>
<tr>
<td>izquierda</td>
<td><em>&amp;&amp;</em></td>
<td><a href="http://php.net/manual/es/language.operators.logical.php">lógico</a></td>
</tr>
<tr>
<td>izquierda</td>
<td>_</td>
<td></td>
</tr>
<tr>
<td>derecha</td>
<td><em>??</em></td>
<td><a href="http://php.net/manual/es/language.operators.comparison.php">comparación</a></td>
</tr>
<tr>
<td>izquierda</td>
<td><em>? :</em></td>
<td><a href="http://php.net/manual/es/language.operators.comparison.php#language.operators.comparison.ternary">ternario</a></td>
</tr>
<tr>
<td>derecha</td>
<td><em>=</em>  <em>+=</em>  <em>-=</em>  <em>*=</em>  <em>**=</em>  <em>/=</em>  <em>.=</em>  <em>%=</em>  <em>&amp;=</em>  _</td>
<td>=_  <em>^=</em>  <em>&lt;&lt;=</em>  <em>&gt;&gt;=</em></td>
</tr>
<tr>
<td>izquierda</td>
<td><em>and</em></td>
<td><a href="http://php.net/manual/es/language.operators.logical.php">lógico</a></td>
</tr>
<tr>
<td>izquierda</td>
<td><em>xor</em></td>
<td><a href="http://php.net/manual/es/language.operators.logical.php">lógico</a></td>
</tr>
<tr>
<td>izquierda</td>
<td><em>or</em></td>
<td><a href="http://php.net/manual/es/language.operators.logical.php">lógico</a></td>
</tr>
</tbody>
</table><h4 id="operador-de-control-de-errores"><a href="http://php.net/manual/es/language.operators.errorcontrol.php">Operador de control de errores</a></h4>
<p>Se denota @ y se usa para escapar ignorar mensajes de error.</p>
<pre><code>$value = @$cache[$key]; // no producirá una anotación si el índice $key no existe.
</code></pre>
<h2 id="estructuras-de-control"><a href="http://php.net/manual/es/language.control-structures.php">Estructuras de control</a></h2>
<p>Son estructuras que permiten modificar el flujo de ejecución de las instrucciones un programa.</p>
<h3 id="if"><a href="http://php.net/manual/es/control-structures.if.php">if</a></h3>
<p>Permite validar si una expresión es verdadera, en caso de ser así ejecuta las sentencias dentro de las llaves, en caso de que no se cumpla la la condición el programa seguirá su flujo normal.</p>
<pre><code>if (expr) {
  sentencia
}
</code></pre>
<h3 id="if-else"><a href="http://php.net/manual/es/control-structures.else.php">if else</a></h3>
<p>Al igual que la estructura <strong>if</strong> valida si la expresión es válida, en caso de ser verdadera se ejecuta el primer grupo de sentencias, en caso de que no se ejecutará el siguiente grupo de sentencias.</p>
<pre><code>if (expr) {
    sentencia
} else {
    otra_sentencia
}
</code></pre>
<h3 id="if-elseif"><a href="http://php.net/manual/es/control-structures.elseif.php">if elseif</a></h3>
<p>Se pueden encadenar una serie de if elseif para hacer una serie de validaciones con la profundidad necesaria, valida la expresión del if, si es verdadero ejecuta el primer bloque de sentencias, si no valida una segunda expresión, que en caso de ser verdadera, ejecuta el segundo bloque de sentencias, a continuación si no se especifica un else o elseif nuevamente, el flujo del programa continua normalmente.</p>
<pre><code>if (expr) {
    sentencia
} elseif(expr2) {
    otra_sentencia
}
</code></pre>
<h3 id="sintaxis-alternativa-para-sentencias-ifif-elseif-elseif">Sintaxis alternativa para sentencias if/if else/if elseif</h3>
<p>Si bien en las primeras versiones de php se usaban las llaves <strong>{ }</strong> para delimitar un bloque de sentencias, las versiones más recientes también proporcionan una segunda sintaxis que usa <strong>:</strong> (dos puntos) y una palabra reservada de cierre.</p>
<p>Así se vería un if else con esta sintaxis:</p>
<pre><code>if(expr):
    sentencia
else:
	otra_sentencia
endif;
</code></pre>
<h3 id="while"><a href="http://php.net/manual/es/control-structures.while.php">while</a></h3>
<p>La estructura <strong>while</strong> corresponde al grupo de <strong>bucles (loops)</strong>, es la más básica, esta funciona iterando la sentencia que se encuentra dentro del bloque mientras la expresión pasada sea válida.</p>
<pre><code>while(expr) {
    sentencia
}
</code></pre>
<p>De forma alternativa podemos usar la nueva sintaxis:</p>
<pre><code>while(expr):
	sentencia
endwhile;
</code></pre>
<h3 id="do-while"><a href="http://php.net/manual/es/control-structures.do.while.php">do-while</a></h3>
<p>La estructura <strong>do-while</strong> es parecida a <strong>while</strong>, sin embargo esta se diferencia en que esta se ejecuta al menos una vez (ya que while primero verifica la expresión y si se cumple itera).</p>
<pre><code>do {
	expresion
} while(expr);
</code></pre>
<p>De forma alternativa podemos usar la nueva sintaxis:</p>
<pre><code>do :
	expresion
while(expr);
</code></pre>
<h3 id="for"><a href="http://php.net/manual/es/control-structures.for.php">for</a></h3>
<p>Esta estructura también es de bucle, sin embargo cuenta con una sintaxis un poco más compleja y normalmente se usa cuando de antemano conocemos cuántas veces debe iterar.</p>
<pre><code>fo(expr1; expr2; expre3) {
	sentencia
}
</code></pre>
<p>expr1 se evalúa sólo una vez y es al inicio de la ejecución del for.<br>
expr2 se evalúa en cada inicio de iteración y evalúa si se debe iterar una vez mas.<br>
expr3 se evalúa una vez que se ejecutó la sentencia.</p>
<p>Cada parte puede ser vacía o puede tener más de una expresión separada por comas, sin embargo si expr2 se deja vacía al ser la bandera de la iteración se hará un bucle infinito.</p>
<p>Normalmente expr1 se usa para inicializar la variable de control, expr2 hace la evaluación y expr3 es el de incremento/decremento.</p>
<p>Por ejemplo.</p>
<pre><code>fo($i = 0; $i &lt; n; $i++) {
	sentencia
}
</code></pre>
<p>For también permite la nueva sintaxis:</p>
<pre><code>fo(expr1; expr2; expre3):
	sentencia
endfor;
</code></pre>
<h3 id="foreach"><a href="http://php.net/manual/es/control-structures.foreach.php">foreach</a></h3>
<p>Esta estructura de bucle es un tanto particular ya que se usa para iterar entre los elementos de un array o un objeto. Existen dos formas de utilizarse:</p>
<pre><code>foreach (expresión_array as $valor) {
    sentencias
}
</code></pre>
<p>Y</p>
<pre><code>foreach (expresión_array as $clave =&gt; $valor) {
    sentencias
}
</code></pre>
<p>De igual forma cuenta con la nueva sintaxis:</p>
<pre><code>foreach (expresión_array as $valor) :
    sentencias
endforeach;
</code></pre>
<h2 id="funciones"><a href="http://php.net/manual/es/functions.user-defined.php">Funciones</a></h2>
<p>Las funciones son como fábricas donde insertas ninguno, uno o varios valores y esta puede retornar uno o ningún valor.</p>
<p>Las funciones son muy útiles para simplificar la lectura del código y para hacer código reutilizable.</p>
<h3 id="sintaxis">Sintaxis</h3>
<p>Su sintaxis es de la siguiente forma:</p>
<pre><code>// Declaración de una función
// Los argumentos pueden ser de cualquier tipo
// Los nombres de función deben cumplir con las mismas restricciones que las variables, aunque estas no deben tener el signo de "$" como primer caracter
function foo($arg_1, $arg_2, /* ..., */ $arg_n) {
	// sentencias
	return $valueReturned;
}
// Ejecución de la función
foo();
</code></pre>
<h3 id="argumentos-con-valores-por-defecto">Argumentos con valores por defecto</h3>
<p>Una buena práctica para evitar errores es el de asignar valores predefinidos a a los argumentos, esto se logra asignando con el operador “=” el valor que va a adoptar el argumento en caso de no recibir uno cuando se llame a la función:</p>
<pre><code>function funcionConValorPredefinido($arg = 1) {
	echo $arg;
}
funcionConValorPredefinido(); // Muestra "1"
funcionConValorPredefinido(5); // Muestra "5"
</code></pre>
<h3 id="argumentos-variables">Argumentos variables</h3>
<p>PHP cuenta con un operador llamado <strong>splat</strong>, este permite habilitar a una función para que reciba una cantidad indefinida de argumentos, su sintaxis es la siguiente:</p>
<pre><code>function funcionConArgumentosVariables(...$array)
{
	// sentencias
}
</code></pre>
<p>Donde $array es un array indexado;</p>
<h3 id="declaraciones-de-tipo">Declaraciones de tipo</h3>
<p>En versiones más recientes es posible asignar <strong>tipos</strong> a los argumentos y al valor de retorno:</p>
<pre><code>function funcionConTipos(array $arg): string {
	// sentencias
	return 'Mi cadena';
}
funcionConTipos([1, 2, 3]); // Muestra "3"
</code></pre>
<h3 id="declaraciones-de-tipo-de-argumentos-variables">Declaraciones de tipo de argumentos variables</h3>
<p>Cuando se declara un tipo para los argumentos variables tiene un comportamiento bastante especial:</p>
<pre><code>function funcWithVariableTypedVars(string ...$array)  
{  
	echo json_encode($array);
}
funcWithVariableTypedVars(1, "10", "2.2", false); // Muestra ["1", "10", "2.2", ""]
</code></pre>
<p>Como se puede ver en el ejemplo al pasarse todos los argumentos a un array, estos se intentan convertir a cadena. Así se puede ir experimentando con los diferentes tipos primitivos.</p>
<h3 id="funciones-recursivas"><a href="http://php.net/manual/en/functions.user-defined.php#example-135">Funciones recursivas</a></h3>
<p>Funciones recursivas se les llama a las funciones que se llaman a sí mismas, estas funciones son útiles cuando se requiere que una misma acción se repita hasta que se cumpla cierta condición;</p>
<pre><code>function factorial(int $n): int  
{  
	if($n == 1) :
	    return 1;  
	else :
		return $n * factorial($n - 1);
	endif;
}
$result = factorial(3);  
echo $result; // Muestra 6
</code></pre>
<h3 id="callbacks"><a href="http://php.net/manual/es/language.types.callable.php">Callbacks</a></h3>
<p>Los callbacks son funciones que se pasan como argumento de otras funciones y normalmente se utilizan para ejecutar una acción una vez que haya terminado la ejecución de las sentencias de la función que la ha llamado.</p>
<pre><code>function myFunctionWithCallback($data, callable $callback)
{
    // sentencias 
    call_user_func($callback, $data);
}
myFunctionWithCallback(1, function($data) {
    var_dump($data);
});
</code></pre>

