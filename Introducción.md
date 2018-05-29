---


---

<h1 id="introducción">1. Introducción</h1>
<h2 id="convenciones">Convenciones</h2>
<ul>
<li>En lo posible cada término cuenta con un vínculo a la documentación oficial de PHP en español donde se podrá encontrar detalles con mayor profundidad</li>
<li>El presente curso parte de que se está trabajando con una distribución de Linux Ubuntu 18.04</li>
<li>La versión de PHP que se usará es la 7.2.x que es la que instala por default el repositorio que tiene Ubuntu 18.04</li>
<li>Cada nuevo término nuevo incluido será resaltado en negritas o con un vínculo a su documentación</li>
</ul>
<h2 id="¿qué-es-php-y-mysql">¿Qué es <a href="http://www.php.net/">PHP</a> y <a href="https://www.mysql.com/">MySQL</a>?</h2>
<p>PHP es un <strong>lenguaje de programación interpretado del lado del servidor</strong>, es decir, el código es interpretado en una computadora remota y el resultado es enviado al navegador del usuario para que este se encargue de mostrar la información enviada.</p>
<p>PHP es un lenguaje que distingue entre mayúsculas y minúsculas (<strong>case sensitive</strong>), no es lo mismo $miVar y $MiVar.</p>
<p>Así mismo es un <strong>lenguaje bloqueante</strong>, es decir no ejecuta una instrucción si no ha terminado la previamente ejecutada, a diferencia de lenguajes como <strong>JavaScript</strong> que cuenta con procesos asíncronos.</p>
<p>Por otro lado <strong>MySQL</strong> es un <strong>Gestor de Base de Datos (DBMS)</strong> para <strong>Bases de Datos Relacionales</strong> que permite escribir y consultar información de forma rápida y sencilla.</p>
<p>En conjunto son un par de tecnologías que suelen encontrarse en una enorme cantidad de proyectos para realizar sitios o servicios web de pequeñas empresas o grandes corporaciones.</p>
<h2 id="¿qué-es-un-servidor-web">¿Qué es un servidor web?</h2>
<p>Un servidor web es un programa encargado de gestionar la comunicación entre las peticiones que se le realiza un usuario a un servidor.</p>
<p>Generalmente la comunicación entre ambas partes es realizada a través del protocolo <strong>HTTP</strong>.</p>
<h2 id="preparación-de-ambiente-de-desarrollo">Preparación de ambiente de desarrollo</h2>
<p>Para este curso vamos a usar un ambiente <strong>LAMP (Linux, Apache, MySQL y PHP)</strong>.</p>
<h3 id="instalar-ambiente-lamp">Instalar ambiente LAMP</h3>
<pre><code>// Update Ubuntu
sudo apt-get update
// Install Apache Server
sudo apt-get install apache2 -y
// Install MySQL
sudo apt-get install mysql-server -y
sudo mysql_secure_installation
// Install PHP
sudo apt-get install php libapache2-mod-php php-mysql -y
</code></pre>
<h3 id="agregar--index.php">Agregar  index.php</h3>
<pre><code>sudo vimmo /etc/apache2/mods-enabled/dir.conf

&lt;IfModule mod_dir.c&gt;
    DirectoryIndex index.php index.html index.cgi index.pl index.php index.$
&lt;/IfModule&gt;
</code></pre>
<h3 id="reiniciar-servidor">Reiniciar servidor</h3>
<pre><code>sudo service apache2 restart
</code></pre>
<h3 id="instalar-phpstorm">Instalar <a href="https://www.jetbrains.com/phpstorm/download/">PhpStorm</a></h3>
<ul>
<li>Descargar PhpStorm</li>
<li>Descomprimir la carpeta donde queremos que se instale</li>
<li>Entrar a la carpeta descomprimida</li>
<li>Entrar a la carpeta bin</li>
<li>Ejecuta el comando <code>./phpstorm.sh</code></li>
<li>Seguir las instrucciones de instalación</li>
</ul>
<h3 id="instalar-mysql-workbench">Instalar <a href="https://www.mysql.com/products/workbench/">MySQL Workbench</a></h3>
<p>Seguir las instrucciones por del instalador.</p>

