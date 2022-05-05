# Resumen proceso de aprendizaje
Este documento resume el proceso de aprendizaje en clase a lo largo de todo el curso que llega hasta el momento presente. El contenido recogido está extraído de mis notas de clase y experiencia en la terminal. 

## Introducción
La dirección del proceso de aprendizaje no es lineal sino que, siendo progresiva, es constantemente circular. Las operaciones aprendidas y la lógica detrás de las sintaxis trabajadas son tereas acumulativas e intrísicamente relacionadas que no se aprenden de una en una sino en diálogo con el resto de funciones (o comandos, o tipos de lenguajes o de datos...según de lo que estemos hablando) y con el entorno en que nos estemos moviendo. Pero incluso decir que se aprenden de esta manera resulta falaz, pues no son conocimientos ni tareas en su mayoría que puedan darse por aprendidas como puede darse por aprendido sumar. Son conocimientos y tareas que solo se adquieren y aprenden en el proceso de realizarlas y que constantemente exigen volver a la casilla de salida (aún siendo imposible hablar en términos de inicio y final). Me refiero por ejemplo a volver a introducir `pwd` en la terminal hasta el último minuto del curso o a crear un nuevo repositorio en Github con el que trabajar. Me refiero al proceso por el que las prácticas no pueden darse por terminadas porque se siguen construyendo en el proceso de realizarlas y las modificaciones en el documento .md alteran la base sobre la que partía el nuevo trabajo.

Con todo esto quiero subrayar que el resumen que contienen estas líneas es un proceso de aprendizaje contínuo en primera persona que se escribe no desde la meta final, sino desde un medio camino hacia un destino tan incierto como fructífero que en su proceso de realizarse **se está realizando** y aprendiendo. Por lo que estas líneas son el reflejo del proceso de aprendizaje de todo el curso, pero también un proceso de aprendizaje en sí mismo que solo se realiza en presente contínuo en el acto mismo de **estar escribiendo**.

## Instalación de un programa de emulación de la terminal
De lo primero que hicimos en clase fue instalar la temrinal **Ubuntu** desde **Power Shell**, un programa que emula la terminal desde la que lanzar comandos con un lenguaje específico llamado Shell. Este lenguaje tiene dialectos: **bass**, que es el que usamos en Windows y **zsh** para mac. En la raíz del sistema del ordenador tenemos dos rutas: **/bin/bash**. La primera es una carpeta o directorio, la segunda un binario. Un binario es el programa que ejecuta la terminal, los archivos que puede ejecutar un sistema operativo determinado. La terminal es el mando de la línea de comandos. Nos descargamos una virtualización de **Linux en Windows** así: `wsl --install -d Ubuntu`. Posteriormente nos descargamos **Cygwin**, el emulador de la terminal en Posix. Ofrece un cojunto de herramientas y programas que emulan una distribución Linux en Windows. La primera vez que lo usamos descargamos `lynx`, un navegador en línea de comandos. Su estructura es `comando-opciones-argumentos`. 

## Configuración del programa
Una vez instalada la terminal la configuramos. Puesto que la terminal pasó de Ubuntu a Cygwin contaré el proceso de aprendizaje sobre esta última. En el instalador de la terminal introdujimos los siguientes cambios que nos permitían descargar la terminal ya configurada, al menos parcialmente:

- `lynx`
- `libssl`
- `man-db`
- `openssl`
- `tzcode`
- `tzdata`
- `ca-certificates`
- `gnupg`
- `libassuan0`
- `libbrotlicommon1`
- `librotlicdec1`
- `libcares2`
- `libcom`

Una vez añadidos estos cambios en el instalador confirmamos la instalación. Para completar su proceso de configuración nos faltaba poder cambiar la **HOME**, una variable de entorno, el espacio de trabajo de nuestra terminal, definido en el archivo de configuración de la misma: **bash.rc**. Necesitábamos por tanto editar este documento, para lo cual necesitabamos el editor de texto **nano**, que como puede comprobarse arriba se nos olvidó descargar y era precisamente el motivo por el que cambiamos de Ubuntu a Cygwin. Además, para poder instalarnos el nano necesitábamos primero instalar el gestor de paquetes y programas del emulador de la terminal, **apt-cyg**. Este gestor de paquetes funciona en la línea de comandos y es la herramienta para instalar todas las demás y que posibilita que no tengamos que volver al instalador de Cygwin cada vez que queramos añadir o modificar algo. El proceso de configuración del editor de texto nano y del gestor de paquetes y programas de la terminal será resumido posteriormente.

Una vez tuvimos nano pusimos `nano /etc/nsswicht.conf` y se abrió la interfaz de nano con este documento. En él pusimos `db_home:windows` para cambiar la home y hacerla coincidir con la de Windows. Guardamos los cambios, salimos del documento y cerramos la terminal, pues el cambio introducido cambia la configuración de la misma y no basta con `enter` para ejecutar el cambio. Necesitamos reiniciarla. Al abrirla de nuevo vemos que la home ha cambiado: `/cygdrive/c/Users/Terese`. Con un `ls` comprobamos que está todo nuestro espacio de Windows. Es interesante establecer un alias para la HOME, un atajo para llegar a ella más rápido.  Para ello editamos el archivo de configuración de Bash (`$HOME /bash.rc`) para decirle que nos devuelva (con el comando `echo`) un alias (opción) de micasa (argumento) en este documento ($HOME/bash.rc). El resultado de esta sintaxis es `echo alias micasa='mnt/c/Users/Terese/Desktop/UC3M/5/2/Periodismo\ de\ datos/'`. Se habría generado el alias **micasa** con el que terminábamos de configurar la Home y la terminal para configurar el nano.

## Configuración de un programa de edición de texto 
Una vez instalado el nano, (`apt-cyg install nano`) necesitábamos configurarlo para poder trabajar con él. Para ello debíamos acceder al documento nano de su propia configuración (**nanorc**) y alterar condiciones que por defecto vienen dadas. Para acceder a dicho documento podemos o bien con `$HOME.nanorc` desde la home recién cambiada, (pues `$` indica que es una variable de entorno de este programa), o bien copiamos el documento nanorc de configuración que ya teníamos en Ubuntu aquí. Para ello: `cp /etc/nanorc .nanorc`. Si accedemos directamente a este documento (porque no existiera de antes un archivo configurado, no lo encontremos o queramos volver a crearlo) alteramos la configuración así: eliminamos los "##" que preceden la línea `set softwrap` y `set linenumbers` que pasan a activarse y ponerse en verde (en vez de en azul como el resto del documento) para condensar la longitud del texto al tamaño de nuestra pantalla por un lado y numerar las líneas por otro y poder utilizar por tanto el nano como editor de texto.

## Configuración y funcionamiento de un gestor de paquetes/programas del emulador de la terminal
Una vez instalada la terminal necesiamos configurar el gestor de paquetes y programas del emulador de Cygwin. Esto es un binario o programa que ejecuta la terminal. Contiene los archivos que puede ejecutar un sistema operativo determinado. En el caso de Ubuntu es `apt`. En el caso de Cygwin es **apt-cyg**. Para poder instalarlo ponemos `lynx -source rawgit.com/transcode-open/apt-cyg/master/apt-cyg > apt-cyg`. El significado de esta sintaxis es que ejecutará `lynx` con la opción `-source` para descargar el código fuente de la página `'rawgit.com/transcode-open/apt-cyg/master/apt-cyg'` y ese texto lo envía con `>` al archivo apt-cyg. Estamos creando así en el directorio/carpeta/ruta donde estemos un archivo con nombre "apt-cyg" que contiene el texto del código fuente de esa URL: un script para usar Cygwin e instalar programas sin correr manualmente el instalador. Comprobamos que está con un `ls`. Ahora que hemos importado el código fuente de la página podemos ejecutar la instalación. Para ello: `install apt-cyg /bin`. Con `install` estamos instalando el archivo apt-cyg, que es un programa, en la carpeta bin, que son los programas o binarios.

## Versión del lenguaje de SHELL utilizado
Para conocer la versión del lenguaje **SHELL** que utiliza la terminal tenemos que formular la pregunta para que nos responda. El comando para la impresión de un texto en pantalla es `echo`. ¿Qué queremos saber? la versión del lenguaje SHELL utilizado **en este programa**. Esto significa que se trata de una variable de entorno. Por tanto: `echo $SHELL`. Me responde: "**/bin/bash**". Esto concuerda lógicamente con la compresión teórica que subyace en este proceco: bash es el lenguaje de programación de SHELL en Windows. /bin/bash son las rutas integradas en la raíz del ordenador que responden al caracter de directorio, carpeta o repositorio y al de binario, el programa que gestiona dichos contenidos. 

## Valor de la variable de entorno PATH
La variable de entorno **PATH** me dice los archivos y programas que puedo configurar. Para ello: `echo $PATH`.
Una de las configuraciones más importantes para trabjar fue la configuración de **Git** para poder trabajar en Github (online) desde mi directorio (local). Para ello: `git config --global user.name"teresa-lopez-lopez"`, y `git config --global user.email"100386353@alumnos.uc3m.es"`.

## Comandos utilizados y ejemplos
Primero listaré los comandos aprendidos para aportar un ejemplo de su posible uso. Incluiré también algunas de las opciones y argumentos de los comandos más destacados en el curso por lo que recuérdese que su estructura es comandos-opciones-argumentos. Entre estos siempre va un espacio. 
 
- `whoami` -> saber quién soy. Mi usuario. Salida comando: /home/teresalopez
- `pwd` -> saber dónde estoy. Mi directorio de trabajo.
- `cd` -> cambiar de directorio, moverme por el ordenador desde la terminal.
	- `cd -` -> volver al último sitio en el que estaba.
	- `cd ./` -> situarme en una carpeta dentro del lugar en que me encuentro.
- `cat` -> concatenar archivos y crear url. Cat necesita argumentos, no como pwd. Por ejemplo: `cat /etc/hosts`.
- `ls` -> listar los archivos de un directorio.
	- `ls -a` -> ver archivos ocultos como nano.rc. 
	- `ls /mnt` -> ver dónde están mis archivos.
	- `ls /mnt/c` -> ver el disco duro.
		- Por ejemplo `ls /mnt/c/Users/Terese/Desktop/UC3M/5/2/Periodismo\ de\ datos`
- `mkdir` -> crear un directorio.
- `mv` -> mover o renombrar archivos.
- `cp` -> copiar un archivo o directorio. Ruta de origen y destino (/).
- `rm` -> eliminar archivos.
- `man` -> saber el número de opciones del mismo. Es un manual.
	- `man ls` -> conocer las  opciones de un comando.
		- `man ls|less` -> pasar la salida de un comando a otro
- `more` -> ver el contenido de un archivo. Por ejemplo `more README.md`
- `nano` -> editar el texto de un archivo .md.
	- `nano $HOME/ nanorc` -> para editar el archivo de configuración de nano. Otras opciones son:
	- `nano ~/` : el `~/` otra forma de llamar a mi Home.
	- `nano /mnt/c/Users/Terese...`
- `grep` -> para encontrar texto en el archivo que le indiquemos.
- `env` -> ver todas las variables de entorno.
	- `env|less|$HOME` -> ver cuál es mi espacio de usuario.
	- `env|less|$PATH` 
- `echo` -> impresor de texto en terminal.
	- `echo $HOME` -> ver cuál es mi casa.
	- `echo $PATH` -> ver qué archivos y programas puedo configurar.
	- `echo $SHELL` -> ver el lenguaje de programación utilizado.
	- `echo $url` -> evocar una url definida.

`git`
	- `git clone` -> clonar un repositorio.
	- `git remote` -> crear, ver y eliminar conexiones con otros repositorios.
		- `git remote -v`-> ver qué repositorios puedo bajar (**fetch**) y subir (**push**).
		- `git remote add origin url` -> agregar un repositorio remoto.
	- `git status` -> saber en qué estado me encuentro.
	- `git add ` -> añadir a un directorio en una ruta los cambios guardados.
	- `git commit -m ""` -> comitear lo cambios, ponerles el sello.
	- `git push` -> subirlos a GitHub.
	- `git config` -> configurar git y conectar GitHub con el ordenanor. 
		- `git config --global user.name` -> configurar el nombre de usurario. 
		- `git config --global user.email` -> configurar el email.
		- `git config --global core.editor nano` -> configurar el editor de texto.
		- `git branch` -> gestión de ramas.
		- `git branch -m main` -> renombrar la rama actual *main*. 

### Comandos terminal forma
Teclado
- `ctrl-a` -> mover cursor.
- `ctrol-d` -> borrar lo escrito.
- `ctrl-g` -> abortar un proceso (salir del bucle de cat, por ejemplo).
- `ctrl-o` -> guardar.
- `ctrl-x` -> salir.

Operadores 
- `&&` -> para llevar a cabo varias acciones en la terminal. Por ejemplo: `mkdir repositorio && cp repositorio`.
- `|` -> pasar de una salida a una entrada.  

Sintaxis 
- `~` -> atajo de ruta, para referirnos al contenido del texto. 
- `~/` -> atajo de ruta para llamar a mi Home.
- `.` -> para situarnos dentro del contenido.
- `$` -> forma de evocar variables de entorno en Bash.
- `>` -> envía la salida del comando a donde indique.
- `>>` -> envía la salida del comando al final del archivo que indique y si no existe lo crea.

### Caso práctico
Para representar la utilidad de los comandos recrearé cómo podría actualizar [mi repositorio](https://github.com/Teresalopezlopez/Practicas-Periodismo-Datos) de las prácticas de la asignatura con el fin de añadir la práctica 4 y actualizar las anteriores. Desde la terminal en primer lugar preguntaría donde estoy y me cambiaría de directorio: 
- `pwd`
- `cd /mnt/c/Users/Terese/Desktop/UC3M/5/2/Periodismo\ de\ datos`

A continuación copiaría el repositorio remoto para conectarlo con mi terminal:
- `git clone https://github.com/Teresalopezlopez/Practicas-Periodismo-Datos`

Entro en dicho repositorio
- `cd ./Practicas-Periodismo-Datos`

Listo los archivos para verlos claro
- `ls`

Edito el README.md para añadir la práctica 4 en la explicación.
- `nano README.md` 

Elimino todos los demás archivos del repositorio, pues todos han cambiado:
- `rm practica-1-tresca.md`
- `rm practica-1-libre.md`
- `rm practica-2.md`
- `rm practica.3.md`
- `rm api-pandas-folium.html`
- `rm api-pandas-folium.ipnyb`
- `rm python-api-covid19-pandas.ipnyb`
- `rm python-api-covid19-pandas.html`
- `rm archivo-datos-practica-3.csv`
- `rm probando-con-r.html`
- `rm probando-con-r.ipnyb`

Puedo borrarlos juntos en una acción. Cambio de directorio, al que contiene el repositorio final para copiar todos sus archivos excepto el README.md, resumen.md, metodología.md y _config.yml.
- `cd -`
- `cd ./teresa-lopez-lopez`
- `cp practica-1-tresca.md practica-1.libre.md practica-2.md practica-3.md practica-4.md practica-4.csv api-pandas-folium.html api-pandas-folium.ipnyb esvsit.csv esvsitvsmx.png practica-4-grafico.png python-api-covid19-pandas.html pyhton-api-covid19-pandas.ipnyb python-csv-pandas.html pyhton-csv-pandas.html /mnt/c/Users/Terese/Desktop/UC3M/5/2/Periodismo\ de\ datos/Practicas-Periodismo-Datos/'

Compruebo que se haya copiado, para ello cambio de directorio:
- `cd -`
- `cd ./Practicas-Periodismo-Datos`
- `ls`

Me detengo en observar si está como lo quiero. Puedo revisar todos los documentos .md con nano y si no falta nada procedo a subir. 
- `git add .`
- `git commit -m "commit"`
- `git status`
- `git push`
	-usuario
	-token
Reviso desde Github si está como quiero. 
