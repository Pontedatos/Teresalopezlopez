# Metodología 
Este archivo documenta cómo he creado este repositorio y la estructura web a él ligada. 

## Creación Repositorio
En primer lugar, desde mi cuenta **Github** he creado un nuevo repositorio y lo he situado en **Pontedatos** con mi nombre. Así he generado la dirección que me permitiría trabajar con la terminal: `github.com/Pontedatos/teresa-lopez-lopez`. Lo creé con un documento **README.md**.

## Desde la terminal
Desde la terminal he clonado el repositorio remoto para conectarlo con el local. Lo he hecho en una carpeta de trabajo diferente a la que he utilizado durante todo el curso y he movido el contenido de dicha carpeta a la recién llegada. Para ello he utlizado los distintos comandos:

- `pwd`para situarme.
- `cd`para cambiar de directorio.
- `rm` para eliminar archivos.
- `mkdir`para crear la nueva carpeta de trabajo.
- `git clone` para clonar en ella el repositorio remoto.
- `cd -` para volver al directorio de trabajo anterior.
- `mv` para mover y renombrar los archivos.
- `nano` para editar los textos

Sin embargo, si no hubiera creado el repositorio con un **README.md** no hubiese sido posible establecer la conexión entre ambos espacios de trabajo. Esto lo supe tras haberlo hecho. En su defecto, y como hice para la práctica 2, la sintaxis para crear el repositorio desde la terminal es la siguiente:

- `echo "# nombre repositorio" >> README.md`
- `git init`
- `git add README.md`
- `git commit -m "first commit"`
- `git branch -M main`
- `git remote add origin https://github.com/Teresalopezlopez/nombre-repositorio-.git`
- `git push -u origin main`

Mientras lo hacía he ido cambiando y corrigiendo con `nano` cosas de todas las prácticas. Sobre todo los documentos ´.md´ explicativos con los enlaces relativos. 
- En la **práctica 1** he incorporado una imagen desde la terminal y revisado el contenido y forma de la práctica.
- En la **práctica 2** he vuelto a incorporar las imágenes desde la terminal especificando mejor las palabras que se muestran del enlace para que si una persona ciega leyese el documento la imagen no fuese una interrupción incoherente en la lectura, sino que a través de ellas pudiese entender que ahí va una imagen y qué información aporta.
- He hecho un repaso de los cuadernos de la **práctica 3** en Jupyter. Al repasarlos he sabido y entendido muchas cosas que en el momento de la entrega desconocía y he intentado avanzar un pasito más: en el cuaderno de la práctica sobre los accidentes de tráfico en Zaragoza, por ejemplo, he procedido a la representación en el mapa de los accidentes del dataframe con marcadores. Finalmente he decidido eliminar dos de los cuadernos entregados y entregar los otros dos. Esto se debe a que las funciones que recogían los dos primeros se repiten en los dos segundos, mucho más completos y extensos. 
- He realizado la **práctica 4** intentando poner en práctica todo lo aprendido para obtener un resultado coherente con los datos y práctico para recoger una información interesante.
Tras un largo proceso de recopilación, orden y trabajo con contínuas actualizaciones, cuando he tenido en la nueva carpeta de trabajo todo el contenido del curso lo he subido a **GitHub** con los siguientes comandos:
- `git add .` 
- `git commit -m "..."`
- `git status`
- `git push`
	- User
	- Token

## Repositorio final
He comprobado que los cambios se hubieran volcado en `pontedatos/teresa-lopez-lopez` y así había sido. Pero los enlaces no funcionaban porque no había escrito bien la sintaxis relativa. Eso me llevó a cambiar los enlaces desde el nano en la terminal de los documentos `.md` y puse sus enlaces absolutos copiándolos de su ruta git. Posteriormente esto tendría que cambiar de nuevo. He aprovechado para repasar todo de nuevo. Con los pasos anteriores he vuelto a subir el contenido. 

## Hacia la estructura web
Tras asegurarme de que los cambios se habían realizado y de que los links funcionaban he procedido a la creación de la estructura **web**. Para ello he acudido al apartado **settings** de mi repositorio y en la pestaña *Pages* he seleccionado `main` en la carpeta root. He elegido la fuente *minimal* por su aspecto de orden y Github ha generado así una web que ha convertido el README.md en `index.html` y el resto de archivos .md en **html**. El resultado el la web con la apariencia minimal muestra mi nombre y descripción del repositorio así como el contenido del README.md con sus respectivos enlaces a las prácticas del curso. Pero me doy cuenta en tutoría de que esto no puede hacerlo porque los enlaces son absolutos y no relativos. Aprendo la sintaxis correcta de los mismos. Vuelvo a cambiar todos los enlaces en los documentos ´.md´. Repaso todo. Sigo introduciendo y cambiando prácticas. Compruebo que los enlaces funcionan.

## Últimos pasos 
La estructura web requerida para este trabajo puede verse [aquí](https://pontedatos.github.io/teresa-lopez-lopez/). Por ello vuelvo a la terminal para crear el documento que contiene estas líneas narrando el proceso de creación. Tras ello, crearé el documento *resumen.md*, último de los procesos a documentar, y volveré a subir los cambios desde la terminal mediante el proceso señalado. Finalmente actualizaré las prácticas en el repositorio en el que llevo trabajando todo el curso para añadir la práctica 4 e incorporar las últimas versiones corregidas de las anteriores.
