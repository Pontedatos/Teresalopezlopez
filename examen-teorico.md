# Examen Teresa López

Este es el documento `.md` que responde a la preguntas del examen teórico de la asignatura de **Periodismo de datos** de la alumna **TERESA LÓPEZ LÓPEZ**. Contiene las preguntas comunes, las específicas del **Bloque C** y una pregunta de desarrollo elegida entre las 3 propuestas. 

## Preguntas comunes
  
1. **¿Quién es Philip Meyer?**

**Philip Meyer** es un periodista e investigador en cuyo **Periodismo de Precisión** el **Periodismo de datos** moderno, nacido entre 2006 y 2008, encuentra uno de sus antecedentes. El periodismo de precisión de Meyer fue el primer periodismo que utilizó ordenadores en Estados Unidos y se denominó así para oponerse a un periodismo del estilo de Truman Capote. El periodismo de precisión hace referencia al uso de métodos de análisis de las Ciencias Sociales unido al software estadístico y los ordenadores para construir una historia periodística. A través de su trabajo con los datos, Meyer descubrió, en el contexto de queja por los altos costes de los seguros escolares contra incendios y huracanes en EEUU en el inicio de la década de los 60´s, que el **65% de la financiación de las campañas electorales provenían de los empresarios de los seguros**. El **caso de la CBS en 1952**, la primera retransmisión televisada a escala nacional (estadounidense), trató de predecir los resultados electorales de las elecciones presidenciales americanas con un ordenador (Remington Randen). Junto a otros, este uso del ordenador llevaría al periodismo de precisión al nombre que pervive en la actulidad de *Computer Assisted Reporting* o periodismo asistido por ordenador, uno de los fundamentos del actual periodismo de datos. 

2. **¿Quién fue Florence Nightingale?**

**Florence Nightingale** es, junto a **Charles Minard** (1781-1870) y **John Snow** (1813-1858), una de las personas en las que la **visualización**, una de las tres disciplinas contempladas en el **Periodismo de datos** (periodismo + datos + visualización), encuentra sus antecedentes en el siglo XIX. Nightingale vivió de 1820 a 1910 y fue una enfermera, escritora y estadística, pionera en enfermería moderna y creadora del primer modelo conceptual de enfermería. La **visualización de datos** encuentra en ella uno de sus antecedentes.

## Preguntas específicas: Bloque C
 
1. **¿Cómo creamos un directorio? Si quisiéramos crear dos directorios, ¿podríamos hacerlo de una sola vez? Razona tu respuesta**

Para crear un directorio utilizamos el comando `mkdir` (*make a directory*). Con este comando puedo crear el número de directorios que estime en el mismo nivel del árbol. Al comando le sigue el nombre del directorio a crear, o de los directorios a crear separados por un espacio. Por ejemplo: `mkdir directorio1` o `mkdir directorio1 directorio2`.

2. **¿Cómo vemos los archivos y directorios ocultos al listar un directorio?**

El comando que lista los elementos del directorio en el que estemos situados en la terminal es `ls`. La opción de este comando que lista los archivos y directorios ocultos, como por ejemplo el de configuración del nano (.nanorc), es `-a`. Si además queremos listar los archivos ocultos con detalle utilizamos `ls -la`. Pero la respuesta a la pregunta es `ls -a`. Si quiero listar los archivos de un repositorio en el que no estoy situada en la terminal, o bien me sitúo en él con `cd` o bien pongo la ruta del del directorio en cuestión, como argumento en la estructura del comando. Por ejemplo: `ls -a /ruta`. 

3. **¿En qué se diferencian las rutas absolutas de las relativas? Pon ejemplos de ambas.**

Las rutas absolutas parten de la raíz de la web. Las rutas relativas lo son al lugar o entorno en el que estoy. Por ejemplificarlo con una metáfora, si quiero cambiar a de la facultad de humanidades a la de sociales, bastaría con indicarme que debo cruzar un paso de cebra. Esto sería la ruta relativa al entorno en el que estoy: el Campus de la UC3M en Getafe, Madrid. La ruta absouta comprendería la indicación de que en el planeta Tierra hay 5 continentes, que en uno de ellos, Europa, hay un país España, en cuya capital, Madrid, la Uniersidad Carlos III tiene su sede. Dentro de esta ciudad hay varios campus y lugares distintos y uno de ellos es Getafe. En este campus, la UC3M tiene dos facultades: la de humanidades y la de sociales. Para cambiar de una otra debo cruzar un paso de cebra. De esta manera, la ruta relativa es sólo la última parte de la ruta absoluta, que comprende las coordenadas de todo el entorno general. La traducción de esto en la sistaxis es la siguiente:
- Ruta absoluta: `https://github.com/Pontedatos/teresa-lopez-lopez/blob/main/resumen.md`
- Ruta relativa: `resumen.md`. 
La ruta relativa presupone que va implícito el entorno en que tiene lugar. 

4. **¿Qué función tiene la almohadilla en Markdown y en un programa de la shell? Razona tu respuesta.**

La almohadilla ("#") en Markdown sirve para estructurar el texto, puesto que se trata de un lenguaje de marcas estructurado. (Recordamos que Markdown es la sintaxis simple de **HTML**, lenguaje de marcas de hipertexto). En Markdown, la **almohadilla**, "**#**", es el equivalente del elemento `h1` de HTML o "encabezamiento de primer nivel". El número de almohadillas indica el nivel de encabezamiento que constituye el texto que la prosigue. Así, "# Título1", "## Título2", "### Título3"... por orden de jerarquía (título principal, subtítulo...etc.). En los archivos de configuración de la Shell la almohadilla que aparece al principio de la línea significa que la línea está comentada, es decir, que no la va a leer el programa que quiera leerla para hacer algo. Podemos utilizarla para contar lo que hacemos si cambiamos algo de la configuración de la Shell, como por ejemplo la home:" # Ahora modifico la línea de la variable db_home". Lógicamente, su funcionalidad puede darse a la inversa. Así, podemos transformar líneas comentadas de un archivo de configuración en acciones que lea el programa para aplicarlas. Por ejemplo para configurar el editor de texto nano en el archivo de configuración eliminamos las almohadillas que preceden a las líneas set softwrap y set linenumbers para activarlas (pasan de color azul a verde) con el fin de condensar la longitud del texto al tamaño de nuestra pantalla por un lado y numerar las líneas por otro y poder utilizar por tanto el nano como editor de texto. La diferencia en la función de la almohadilla reside, en el fondo, en que Markdown es un tipo de lenguaje estructurado y Shell utiliza Bash, un lenguaje de programación. Así, en la primera el contenido es código (*content as code*) y la introducción de la "#" lo organiza, y en la segunda por defecto el lenguaje hace cosas a no ser que con la almohadilla le indiquemos lo contrario. 
 
5. **¿Qué es una API? Pon algún ejemplo.**

La **API** es la interfaz de programación de acceso de aplicaciones; algo así como los códigos para comunicarse con una web. En el caso de BASH, sirve para regular el acceso a los datos de BASH (cuyo lenguaje de programación es Shell). Las API´s constituyen una forma más correcta de trabajar con los datos y se utilizan para portales de datos. La API que usamos constantemente es **HTTP**, pero es una API universal. Luego cada recurso, como Twitter por ejemplo, puede tener la suya propia. La Web es una API. El acceso a HTML, CSS y JS es la API, que tiene 4 métodos de acceso: (GET, POST, PUT, DEL). En la API de BASH solo hay 3 métodos: STDIN: entrada estándar de datos, STDOUT: salida estándar de datos y STDER: salida estándar de errores.

6. **¿Qué es Markdown?**

Markdown es dos cosas a la vez:

- Una sintaxis (muy) simple; es decir, una forma de estructurar y marcar el texto de forma sencilla.
- Un conversor de la sintaxis en **HTML**, o "parseador". 
Se tratra de un lenguaje informático de tipo estructurado (html, markdown); frente a los lenguajes informáticos de programación. En el proceso de conversión de markdown a html interviene un lenguaje de programación. El gestor de contenidos o herramienta intermedia que realiza esta conversión en Github es **Jekyll**. En  realidad, Markdown es la lengua franca para la edición de textos en aplicaciones informáticas y nace porque **Dan Gruber** pensó que era difícil de leer el texto de un **código HTML**, el lenguaje de marcas de hipertexto con el que funciona la Web (actualmente la versión 5: HTML5).
 
7. **¿Que significa TSV?**

**TSV** es un formato de archivo de valores separados por tabuladores (*Tab Separated Values*). El formato **CSV** bebe de **TSV**. La diferencia es que CSV separa los datos con comas y TSV con tabuladores. Era necesario el tabulador para separar en algunos casos los datos porque este crea un espacio más grande (4 o 5 caracteres) frente al espacio de la barra espaciadora que deja uno. Los espacios pueden estar presentes en algunos datos, como un nombre o una dirección, pero los tabuladores no. Por eso se utilizaba esta separación para que el ordenador la interpretara como otro campo de la tabla. **Excel** es un programa para visualizar datos tabulados.
## Pregunta de desarrollo

**¿Qué tecnologías confluyen en el nacimiento del periodismo de datos?**

El **Periodismo de Datos** nace posibilitado por la abundancia de 3 tecnologías: 
- Software de código abierto (OSS): modelo de desarrollo descentralizado que distribuye código fuente públicamente para la colaboración abierta.
- HTML5: el lenguaje de marcas estructurado, y 
- Open Data: datos que pueden ser utilizados, reutilizados y redistribuidos libremente por cualquier persona. Se encuentran en bases de datos o ficheros en el ordenador y son fundamentales para el emerger del Periodismo de Datos.
