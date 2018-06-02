---


---

<h1 id="manejo-de-archivos">Manejo de archivos</h1>
<h2 id="operaciones-básicas">Operaciones básicas</h2>
<p>Por defecto PHP ya cuenta con un sistema de manejo de archivos, con el cual podemos abrir, leer y modificarlos.</p>
<h3 id="fopen"><a href="http://php.net/manual/es/function.fopen.php">fopen</a></h3>
<p>Esta función sirve para acceder a un archivo pasándole como primer parámetro la url de dicho archivo y como segundo el modo en el que se accederá a el, y retorna un puntero al archivo en caso de haberlo encontrado y accedido o false en caso de que no haya podido acceder a el.</p>
<pre><code>	$file = fopen("path/to/file", "r");
</code></pre>
<p>Existen once tipos de modos que se le pueden pasar a fopen:</p>

<table>
<thead>
<tr>
<th>modo</th>
<th>Descripción</th>
</tr>
</thead>
<tbody>
<tr>
<td>r</td>
<td>Apertura para sólo lectura; coloca el puntero al fichero al principio del fichero.</td>
</tr>
<tr>
<td>r+</td>
<td>Apertura para lectura y escritura; coloca el puntero al fichero al principio del fichero.</td>
</tr>
<tr>
<td>w</td>
<td>Apertura para sólo escritura; coloca el puntero al fichero al principio del fichero y trunca el fichero a longitud cero. Si el fichero no existe se intenta crear.</td>
</tr>
<tr>
<td>w+</td>
<td>Apertura para lectura y escritura; coloca el puntero al fichero al principio del fichero y trunca el fichero a longitud cero. Si el fichero no existe se intenta crear.</td>
</tr>
<tr>
<td>a</td>
<td>Apertura para sólo escritura; coloca el puntero del fichero al final del mismo. Si el fichero no existe, se intenta crear.</td>
</tr>
<tr>
<td>a+</td>
<td>Apertura para lectura y escritura; coloca el puntero del fichero al final del mismo. Si el fichero no existe, se intenta crear.</td>
</tr>
<tr>
<td>x</td>
<td>Creación y apertura para sólo escritura; coloca el puntero del fichero al principio del mismo. Si el fichero ya existe, la llamada a <strong>fopen()</strong> fallará devolviendo <strong><code>FALSE</code></strong> y generando un error de nivel <strong><code>E_WARNING</code></strong>. Si el fichero no existe se intenta crear.</td>
</tr>
<tr>
<td>x+</td>
<td>Creación y apertura para lectura y escritura; de otro modo tiene el mismo comportamiento que <em>‘x’</em>.</td>
</tr>
<tr>
<td>c</td>
<td>Abrir el fichero para sólo escritura. Si el fichero no existe, se crea. Si existe no es truncado (a diferencia de <em>‘w’</em>), ni la llamada a esta función falla (como en el caso con <em>‘x’</em>). El puntero al fichero se posiciona en el principio del fichero.</td>
</tr>
<tr>
<td>c+</td>
<td>Abrir el fichero para lectura y escritura</td>
</tr>
<tr>
<td>e</td>
<td>Establecer la bandera ‘close-on-exec’ en el descriptor de fichero abierto.</td>
</tr>
</tbody>
</table><h3 id="fclose"><a href="http://php.net/manual/es/function.fclose.php">fclose</a></h3>
<p>Cierra un puntero al archivo abierto, es decir, una vez que decidamos que dejamos de trabajar con un archivo abierto por fopen, podemos finalizar con fclose para cerrar su acceso.</p>
<p>Como único parámetro debe pasársele el puntero del archivo que queremos cerrar:</p>
<pre><code>$file = fopen("/path/to/file", "x");
fclose($file);
</code></pre>
<h3 id="fwritte"><a href="http://php.net/manual/es/function.fwrite.php">fwritte</a></h3>
<p>Escritura de un archivo en modo binario seguro. Se usa para escribir el valore de una variable de tipo cadena sobre un archivo al que ya tenemos previamente un puntero.</p>
<p>Esta función espera tres parámetros:</p>
<ol>
<li>
<p>puntero: puntero al archivo</p>
</li>
<li>
<p>cadena: texto que se insetará en el archivo</p>
</li>
<li>
<p>tamaño (opcional): cantidad máxima de caracteres en la que se detendrá de escribir.</p>
<p>$file = fopen(“path/to/file”, “w”);<br>
$text = “Some text”;<br>
fwritte($file, $text, 300);<br>
fclose($file);</p>
</li>
</ol>
<h2 id="operaciones-de-tratamiento-de-archivos">Operaciones de tratamiento de archivos</h2>
<h3 id="rewind"><a href="http://php.net/manual/es/function.rewind.php">rewind</a></h3>
<p>Vuelve la posición del puntero al inicio del archivo, recibe como único parámetro un puntero.</p>
<pre><code>$file = fopen('salida.txt', 'r+');
fwrite($file, 'Texto a escribir');
rewind($file);
fwrite($file, 'Cadena');
rewind($file);
echo fread($file, filesize('salida.txt')); // Muestra el texto "Cadenaa escribir"
fclose($file);
</code></pre>
<h3 id="feof">feof</h3>
<p>Comprueba si un puntero está al final de un archivo, recibe como parámetro un puntero y retorna un booleano:</p>
<pre><code>$file = fopen('mi-archivo.txt', 'a');
if(!feof($file)) {
	// sentencias
}
</code></pre>
<h3 id="fgets">fgets</h3>
<p>Obtiene una linea desde el puntero de un archivo:</p>
<pre><code>$gestor = @fopen("/tmp/inputfile.txt", "r");  
if ($gestor) {  
	while (($búfer = fgets($gestor, 4096)) !== false) {  
		echo $búfer;  
	}
	if (!feof($gestor)) {  
		echo "Error: fallo inesperado de fgets()\n";  
	}
	fclose($gestor);  
}
</code></pre>
<h3 id="fread">fread</h3>
<p>Lectura de un archivo en modo binario de forma segura.</p>
<pre><code>$nombre_fichero = "/usr/local/algo.txt";  
$gestor = fopen($nombre_fichero, "r");  
$contenido = fread($gestor, filesize($nombre_fichero));  
fclose($gestor);
</code></pre>

