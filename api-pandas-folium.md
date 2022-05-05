# Práctica en el mapa de Zaragoza

En este cuaderno utilizaremos las librerías de **Pandas** y **Folium** para leer una API que importaremos como archivo **.csv** sobre accidentes de tráfico en Zaragoza registrados por su Ayuntamiento. El objetivo es que **Python** lea esos datos para poder explorarlos con distintas funciones para representar la ubicación de los accidentes en un mapa. Lo primero lo podremos hacer con Pandas, una librería de código abierto de Python que proporciona herramientas de análisis y manipulación de datos. Lo segundo lo haremos con Folium, una librería de creación de mapas web interactivos con Python. 

La relación entre ambas librerías para el manejo y representación de este conjunto de datos es que una de sus catergorías es `calle` y sus datos son coordenadas geográficas. De ahí que supongan datos propicios para la combinación de ambas herramientas. 

## Definición de variables

Definimos las variables con las que vamos a trabajar para que Python conozca los datos. Una variable es aquello que puedo crear como tal al nombrarlo. Su sintaxis es `=`, por ejemplo, *x = x*. Vamos a definir como variables los elementos básicos de nuestro trabajo, a saber, los datos (para trabajarlos con Pandas) y las coordenadas geográficas de Zaragoza, escenario de los datos a representar (para hacerlo con Folium).


```python
url_zrgz = "https://www.zaragoza.es/sede/servicio/transporte/accidentalidad-trafico/accidente.csv"
geo_zrgz = [41.646693,-0.887712]
```

Al definir estas variables no es necesario volver a copiar el link cuando queramos vincular los datos, sino que lo haremos con la referencia que hemos creado, en este caso `url_zrgz` y `geo_zrgz`. Como vemos, la sintaxis de la primera es  con `""` y de la segunda con `[]`, puesto que se trata de un intervalo con ambos valores incluidos.

No es imprescindible definir estas referencias en primer lugar, pero sí forma parte de los pasos previos al inicio propiamente dicho del proceso exploratorio de los datos. Podemos resumir estos pasos previos en tres:
1. Definición de variables 
2. Preparación de librerías
3. Creación del dataframe

Procedemos al segundo punto:

## Preparación de librerías

La preparación de las librerías es la condición de posibilidad de nuestro trabajo. Conlleva dos pasos:
- Instalación (`!pip install` *librería*)
- Importación (`import` *librería* o `import` *librería* `as` *su abreviación*)

### Instalación

Solo es necesaria la instalación de la librería que vayamos a utilizar a contunuación. Por lo que no es imprescindible instalar ahora Pandas. Podríamos hacerlo cuando el documento lo requiriese. Pero vamos a tenerla ya preparada. Tampoco es imprescindible instalar librerías si ya lo hemos hecho en otros cuadernos y Python las ha utilizado con anterioridad. Por ello no necesito instalarme Pandas de nuevo. La importación siempre es necesaria. 

Instalo Folium: `!pip install folium`


```python
!pip install folium 
```

    Requirement already satisfied: folium in ./.local/lib/python3.8/site-packages (0.12.1.post1)
    Requirement already satisfied: branca>=0.3.0 in ./.local/lib/python3.8/site-packages (from folium) (0.5.0)
    Requirement already satisfied: jinja2>=2.9 in /usr/lib/python3/dist-packages (from folium) (2.10.1)
    Requirement already satisfied: numpy in /usr/local/lib/python3.8/dist-packages (from folium) (1.21.1)
    Requirement already satisfied: requests in /usr/local/lib/python3.8/dist-packages (from folium) (2.25.0)
    Requirement already satisfied: certifi>=2017.4.17 in /usr/local/lib/python3.8/dist-packages (from requests->folium) (2020.6.20)
    Requirement already satisfied: urllib3<1.27,>=1.21.1 in /usr/lib/python3/dist-packages (from requests->folium) (1.25.8)
    Requirement already satisfied: chardet<4,>=3.0.2 in /usr/lib/python3/dist-packages (from requests->folium) (3.0.4)
    Requirement already satisfied: idna<3,>=2.5 in /usr/lib/python3/dist-packages (from requests->folium) (2.8)


### Importación 

Ahora ya tengo las dos librerías instaladas en Python. Pero eso no significa que las tenga ya aquí en este documento para trabajar con ellas. Para ello necesito importarlas. Por eso, a diferencia que la instalación, que puede realizarse una sola vez, la importación es obligatoria en cada notebook en que quiera usarse. Con el comando `import` importo ambas librerías.La de pandas lo hago con su abreviación típica *pd*.


```python
import pandas as pd
import folium 
```

Una vez tenemos las variables definidas (los datos y las coordenadas) y las librerías preparadas es hora de empezar a trabajar con los datos. Necesito abrirlos desde este documento creando un *dataframe* que los abra. Pero antes (aunque puedo no hacerlo así) abro el mapa para tener presente el espacio en el que quiero proceder a la representación de los datos.

## Mapa Zaragoza

De la librería Folium quiero que Python me muestre un mapa: el folio *map* con las cooredenadas anteriormente señaladas con la referencia `geo_zrgz`.  Definiremos esta acción **mapa_zrgz** con `=`.


```python
mapa_zrgz = folium.Map(location=geo_zrgz)
```

Hemos definido la variable, que a continuación decimos que la ejecute.


```python
mapa_zrgz
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe srcdoc="&lt;!DOCTYPE html&gt;
&lt;head&gt;    
    &lt;meta http-equiv=&quot;content-type&quot; content=&quot;text/html; charset=UTF-8&quot; /&gt;

        &lt;script&gt;
            L_NO_TOUCH = false;
            L_DISABLE_3D = false;
        &lt;/script&gt;

    &lt;style&gt;html, body {width: 100%;height: 100%;margin: 0;padding: 0;}&lt;/style&gt;
    &lt;style&gt;#map {position:absolute;top:0;bottom:0;right:0;left:0;}&lt;/style&gt;
    &lt;script src=&quot;https://cdn.jsdelivr.net/npm/leaflet@1.6.0/dist/leaflet.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;https://code.jquery.com/jquery-1.12.4.min.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;https://cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js&quot;&gt;&lt;/script&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://cdn.jsdelivr.net/npm/leaflet@1.6.0/dist/leaflet.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css&quot;/&gt;

            &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width,
                initial-scale=1.0, maximum-scale=1.0, user-scalable=no&quot; /&gt;
            &lt;style&gt;
                #map_cee2caf1ed7f37f2e9abace160a4150b {
                    position: relative;
                    width: 100.0%;
                    height: 100.0%;
                    left: 0.0%;
                    top: 0.0%;
                }
            &lt;/style&gt;

&lt;/head&gt;
&lt;body&gt;    

            &lt;div class=&quot;folium-map&quot; id=&quot;map_cee2caf1ed7f37f2e9abace160a4150b&quot; &gt;&lt;/div&gt;

&lt;/body&gt;
&lt;script&gt;    

            var map_cee2caf1ed7f37f2e9abace160a4150b = L.map(
                &quot;map_cee2caf1ed7f37f2e9abace160a4150b&quot;,
                {
                    center: [41.646693, -0.887712],
                    crs: L.CRS.EPSG3857,
                    zoom: 10,
                    zoomControl: true,
                    preferCanvas: false,
                }
            );





            var tile_layer_2b6a0e052c0f5e9b6a4394832af54567 = L.tileLayer(
                &quot;https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png&quot;,
                {&quot;attribution&quot;: &quot;Data by \u0026copy; \u003ca href=\&quot;http://openstreetmap.org\&quot;\u003eOpenStreetMap\u003c/a\u003e, under \u003ca href=\&quot;http://www.openstreetmap.org/copyright\&quot;\u003eODbL\u003c/a\u003e.&quot;, &quot;detectRetina&quot;: false, &quot;maxNativeZoom&quot;: 18, &quot;maxZoom&quot;: 18, &quot;minZoom&quot;: 0, &quot;noWrap&quot;: false, &quot;opacity&quot;: 1, &quot;subdomains&quot;: &quot;abc&quot;, &quot;tms&quot;: false}
            ).addTo(map_cee2caf1ed7f37f2e9abace160a4150b);

&lt;/script&gt;" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



Ahora que tenemos este mapa necesitamos que Python lea los datos que queremos que en él represente. La librería que puede hacer esto es **Pandas**. Auqnue tengamos la librería instalada e importada, aún no vemos en este archivo los datos. Tenemos que pedir a Python que con la librería Pandas nos lea los datos. Para ello creamos un dataframe (*df_zrgz*) que será el resultado (esto lo indicamos con *=*) de leer el documento al que lo hemos vinculado. Esto último lo hace con la función `.read_`*tipodocumento*. En este caso vamos a indicarle que es un documento **.csv** aunque los datos no lo sean, porque de esta forma le decimos a Python que cada dato está delimitado por `;`. Al indicarle eso también haremos que el propio Python genere un archivo csv (como podemos comprobar en la interfaz de nuestro servidor) a partir de los datos de la api. 

Una vez indicado el tipo de archivo, corresponde en la sintaxis introducir la referencia del mismo. En nuestro caso es la base de datos, pero no es necesario copiar su link ya que anteriormente la hemos definido como variable, por lo que le damos la referencia (*url_zrgz*). Por último, le especificamos que introduzca los datos delimitados: `pd.read_csv(url_zrgz,delimiter=';')`.

**NOTA**: Un delimitador es una secuencia de uno o más caracteres para especificar el límite entre regiones separadas e independientes en flujos de datos. Así logramos que presente los datos, que no son tabulados, en categorías.


```python
df_zrgz = pd.read_csv(url_zrgz,delimiter=';')
```


```python
df_zrgz
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>year</th>
      <th>type</th>
      <th>accidentType</th>
      <th>firstAddress</th>
      <th>secondAddress</th>
      <th>geometry</th>
      <th>reason</th>
      <th>area</th>
      <th>creationDate</th>
      <th>daniosMateriales</th>
      <th>falloMecanico</th>
      <th>estadoPavimento</th>
      <th>tipoEstadoPavimento</th>
      <th>estadoAtmosfera</th>
      <th>tipoEstadoAtmosfera</th>
      <th>afectado</th>
      <th>vehiculo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>COSTA, JOAQUIN</td>
      <td>PERAL, ISAAC</td>
      <td>-0.8818527060979306,41.649027473051156</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2014-10-09T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>CADENA(MARQUES DE LA)</td>
      <td>NaN</td>
      <td>-0.8645810716721081,41.661585829868585</td>
      <td>DISTANCIA DE SEGURIDAD, no mantener</td>
      <td>2560.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>GOMEZ AVELLANEDA, G.</td>
      <td>CASTRO, R. (POETA)</td>
      <td>-0.887776415002892,41.666992622958105</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2598.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS FRONTOLATERAL</td>
      <td>NaN</td>
      <td>MONZON</td>
      <td>GARCIA CONDOY, H.</td>
      <td>-0.8825260453930127,41.62957498750602</td>
      <td>CEDA EL PASO, no respetar prioridad de paso</td>
      <td>2555.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>RIOJA</td>
      <td>NAVARRA, AVENIDA DE</td>
      <td>-0.908314757720389,41.6562121210704</td>
      <td>PERDIDA del control por VELOCIDAD INADECUADA</td>
      <td>2554.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>5</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>OTRAS</td>
      <td>NaN</td>
      <td>MUEL</td>
      <td>NaN</td>
      <td>-0.8691088511672924,41.65949772773082</td>
      <td>Caída de ocupante en Transporte Público</td>
      <td>2578.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>6</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>ATROPELLO</td>
      <td>NaN</td>
      <td>PIGNATELLI, RAMON VIA</td>
      <td>NaN</td>
      <td>-0.8880337913721866,41.633353667694024</td>
      <td>PEATÓN cruza calz SIN PREFER. fuera de paso</td>
      <td>2606.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>7</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>CAIDA SOBRE CALZADA</td>
      <td>NaN</td>
      <td>ALIERTA, AV. CESAREO</td>
      <td>AULA, LUIS</td>
      <td>-0.8708838775078237,41.6390382112928</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>2583.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>8</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS. MARCHA ATRÁS</td>
      <td>NaN</td>
      <td>CERBUNA, PEDRO</td>
      <td>NaN</td>
      <td>-0.8970649943808023,41.64083344974765</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2556.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>9</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN LATERAL</td>
      <td>NaN</td>
      <td>ASALTO</td>
      <td>COCCI, JORGE</td>
      <td>-0.8718525605769747,41.64904657717317</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>4657.0</td>
      <td>2013-12-20T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>10</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>OTRAS</td>
      <td>NaN</td>
      <td>ARAGON (CORONA DE)</td>
      <td>SAN ANTONIO M CLARET</td>
      <td>-0.8964627561577849,41.64322365075108</td>
      <td>Caída de ocupante en Transporte Público</td>
      <td>63.0</td>
      <td>2013-12-21T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>11</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>FRAGUA, LA</td>
      <td>GASSIER, PIERRE</td>
      <td>-0.8778095796207178,41.68753087470739</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4780.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>12</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>PIRINEOS, AV. DE LOS</td>
      <td>NaN</td>
      <td>-0.8812157329722801,41.661646612715046</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4661.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>13</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>TORRES, CAMINO DE LAS</td>
      <td>NaN</td>
      <td>-0.8762000299022707,41.6454384961757</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4667.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>14</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>ATROPELLO</td>
      <td>NaN</td>
      <td>RIOJA</td>
      <td>NAVARRA, AVENIDA DE</td>
      <td>-0.9089013552408617,41.65543768899759</td>
      <td>PEATÓN cruza calz SIN PREFER. en PASO CON semá...</td>
      <td>4664.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>15</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>ITALIA</td>
      <td>NaN</td>
      <td>-0.9004729973337304,41.65180346604993</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4671.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>16</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>AGUSTIN, PASEO MARIA</td>
      <td>MAYANDIA (GENERAL)</td>
      <td>-0.8917562993466011,41.65233828238132</td>
      <td>DISTANCIA DE SEGURIDAD, no mantener</td>
      <td>18.0</td>
      <td>2013-12-20T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>17</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>AGUSTIN, PASEO MARIA</td>
      <td>SANTA ANA</td>
      <td>-0.888856043735591,41.65040494617356</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4718.0</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>18</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>CASPE, AV.COMPROMISO</td>
      <td>NaN</td>
      <td>-0.8629911318784169,41.645335650478316</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4723.0</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>19</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>MURANO, ISLA DE AV.</td>
      <td>NaN</td>
      <td>-0.8870207060655807,41.609992514227066</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>20</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN LATERAL</td>
      <td>NaN</td>
      <td>HISPANIDAD, RONDA DE</td>
      <td>ALIERTA, AV. CESAREO</td>
      <td>-0.8636325074780108,41.63379905763323</td>
      <td>PUERTA abierta incorrectamente</td>
      <td>17.0</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>21</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>CAIDA SOBRE CALZADA</td>
      <td>NaN</td>
      <td>ZARAGOZA LA VIEJA</td>
      <td>NaN</td>
      <td>-0.8760724207544668,41.63275556609146</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4677.0</td>
      <td>2013-12-21T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>22</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>ASIN Y PALACIOS, MIG.</td>
      <td>NaN</td>
      <td>-0.9036852209830768,41.63808926467497</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2013-12-17T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>23</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLIS. MARCHA ATRÁS</td>
      <td>NaN</td>
      <td>ZAMBRANO, M. (POETA)</td>
      <td>NaN</td>
      <td>-0.8896980442453839,41.677487884305975</td>
      <td>MARCHA ATRÁS</td>
      <td>4783.0</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>24</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>ALBA (DUQUE DE),PASEO</td>
      <td>NaN</td>
      <td>-0.9018264648858587,41.620591734015946</td>
      <td>PERDIDA del control por VELOCIDAD INADECUADA</td>
      <td>4679.0</td>
      <td>2013-12-15T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>25</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLIS FRONTOLATERAL</td>
      <td>NaN</td>
      <td>HISPANIDAD, VIA</td>
      <td>MADRID, AVENIDA DE</td>
      <td>-0.9187726932212442,41.64931371437485</td>
      <td>SEMÁFORO, no respetar prioridad de paso</td>
      <td>4773.0</td>
      <td>2013-12-20T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>26</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN LATERAL</td>
      <td>NaN</td>
      <td>PARAISO, PL.BASILIO</td>
      <td>NaN</td>
      <td>-0.8855988456901538,41.646890443474554</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>4702.0</td>
      <td>2013-12-17T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>27</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN LATERAL</td>
      <td>NaN</td>
      <td>HISPANIDAD, RONDA DE</td>
      <td>NaN</td>
      <td>-0.887523212911549,41.62404668544956</td>
      <td>PUERTA abierta incorrectamente</td>
      <td>4701.0</td>
      <td>2013-12-20T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>28</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN LATERAL</td>
      <td>NaN</td>
      <td>SAGASTA, PASEO DE</td>
      <td>NaN</td>
      <td>-0.8863120908790753,41.63964884250951</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>4700.0</td>
      <td>2013-12-19T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>29</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN LATERAL</td>
      <td>NaN</td>
      <td>CABALDOS, CAMINO DE</td>
      <td>NaN</td>
      <td>-0.8689640327130923,41.638477534601776</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>4752.0</td>
      <td>2013-12-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>30</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>CAIDA SOBRE CALZADA</td>
      <td>NaN</td>
      <td>GOYA,FCO.(PINTOR) AV.</td>
      <td>TORRES MORALES, M.G.</td>
      <td>-0.8900650666830714,41.64332496247496</td>
      <td>DISTANCIA DE SEGURIDAD, no mantener</td>
      <td>4751.0</td>
      <td>2013-12-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>31</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN LATERAL</td>
      <td>NaN</td>
      <td>AGUSTIN, PASEO MARIA</td>
      <td>NaN</td>
      <td>-0.8918524618079099,41.65260977469196</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>4750.0</td>
      <td>2013-12-25T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>32</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>OTRAS</td>
      <td>NaN</td>
      <td>RIOJA</td>
      <td>NaN</td>
      <td>-0.9104038365599549,41.65248328671194</td>
      <td>OTRAS CAUSAS</td>
      <td>NaN</td>
      <td>2013-12-19T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>33</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN LATERAL</td>
      <td>NaN</td>
      <td>CONSTITUCION, PASEO</td>
      <td>PARAISO, PL.BASILIO</td>
      <td>-0.8850103896969528,41.6474034449745</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>2682.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>34</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS. MARCHA ATRÁS</td>
      <td>NaN</td>
      <td>TORRE</td>
      <td>NaN</td>
      <td>-0.8734135018983006,41.64926981833846</td>
      <td>MARCHA ATRÁS</td>
      <td>2626.0</td>
      <td>2014-10-27T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>35</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>ECHEGARAY Y CABALLERO</td>
      <td>MATUTE HERVIAS,JULIAN</td>
      <td>-0.8593239531218387,41.650740541708075</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2605.0</td>
      <td>2014-10-27T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>36</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS FRONTOLATERAL</td>
      <td>NaN</td>
      <td>CABALDOS, CAMINO DE</td>
      <td>CASTELAR, EMILIO</td>
      <td>-0.868891092151338,41.638807389014836</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>2591.0</td>
      <td>2014-10-25T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>37</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>ATROPELLO</td>
      <td>NaN</td>
      <td>ALMOZARA, AV. DE LA</td>
      <td>PUERTA DE SANCHO, AV.</td>
      <td>-0.9008107424460443,41.66374540604866</td>
      <td>PEATÓN cruza calz CON PREFER. en PASO  CON sem...</td>
      <td>2610.0</td>
      <td>2014-10-29T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>38</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS. MARCHA ATRÁS</td>
      <td>NaN</td>
      <td>OLIVAN, ALEJANDRO</td>
      <td>BOSQUED, JOSE (MOSEN)</td>
      <td>-0.9211220937948997,41.64886535549928</td>
      <td>MARCHA ATRÁS</td>
      <td>2594.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>39</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS. MARCHA ATRÁS</td>
      <td>NaN</td>
      <td>ARRUPE, PADRE</td>
      <td>VAZQUEZ DE MELLA</td>
      <td>-0.9026681648170423,41.63265453864093</td>
      <td>MARCHA ATRÁS</td>
      <td>2596.0</td>
      <td>2014-10-20T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>40</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS FRONTOLATERAL</td>
      <td>NaN</td>
      <td>RUIZ PICASSO, PABLO</td>
      <td>ZAMBRANO, M. (POETA)</td>
      <td>-0.8893162332922886,41.67281318904247</td>
      <td>OTRAS CAUSAS</td>
      <td>2640.0</td>
      <td>2014-10-29T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>41</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>ATROPELLO</td>
      <td>NaN</td>
      <td>CAMPOAMOR, CLARA</td>
      <td>NaN</td>
      <td>-0.8890866503471749,41.66895757951277</td>
      <td>PEATÓN cruza calz CON PREFER. en PASO  SIN sem...</td>
      <td>2600.0</td>
      <td>2014-10-29T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>42</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>CASCAJO, CN. DEL  SJN</td>
      <td>NaN</td>
      <td>-0.8439506345833918,41.71496486522088</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2014-10-29T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>43</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>EDISON, TOMAS A</td>
      <td>NaN</td>
      <td>-0.8665477541801948,41.67007665525934</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2014-10-29T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>44</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>CUELLAR, PASEO DE</td>
      <td>NaN</td>
      <td>-0.8848493117953854,41.63484525009101</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2604.0</td>
      <td>2014-10-28T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>45</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN LATERAL</td>
      <td>NaN</td>
      <td>HISPANIDAD, VIA</td>
      <td>GOMEZ LAGUNA(ALCALDE)</td>
      <td>-0.9147014503640727,41.64060309287472</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>2624.0</td>
      <td>2014-10-29T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>46</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>PLAN, IBON DE</td>
      <td>AEROPUERTO, CARRETERA</td>
      <td>-0.9388159722509236,41.66210291413718</td>
      <td>DISTANCIA DE SEGURIDAD, no mantener</td>
      <td>2611.0</td>
      <td>2014-10-27T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>47</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>FANLO</td>
      <td>NaN</td>
      <td>-0.9157439755527074,41.63348367532985</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2631.0</td>
      <td>2014-10-27T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>48</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>AZNAR,ADOLFO(CINEASTA</td>
      <td>BELTRAN,J.M.(CINEASTA</td>
      <td>-0.8869959298557372,41.67593597602368</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4438.0</td>
      <td>2013-12-02T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>49</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>ALLENDE, SALVADOR AV.</td>
      <td>NaN</td>
      <td>-0.876909940066992,41.672106692157605</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4684.0</td>
      <td>2013-12-05T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
  </tbody>
</table>
</div>



Una vez tenemos el dataframe creado lo exploramos con distintas funciones. En primer lugar, `.info` para saber qué contiene el dataframe.


```python
df_zrgz.info
```




    <bound method DataFrame.info of                                                    id  year  \
    0   https://www.zaragoza.es/sede/servicio/transpor...  2014   
    1   https://www.zaragoza.es/sede/servicio/transpor...  2014   
    2   https://www.zaragoza.es/sede/servicio/transpor...  2014   
    3   https://www.zaragoza.es/sede/servicio/transpor...  2014   
    4   https://www.zaragoza.es/sede/servicio/transpor...  2014   
    5   https://www.zaragoza.es/sede/servicio/transpor...  2014   
    6   https://www.zaragoza.es/sede/servicio/transpor...  2014   
    7   https://www.zaragoza.es/sede/servicio/transpor...  2014   
    8   https://www.zaragoza.es/sede/servicio/transpor...  2014   
    9   https://www.zaragoza.es/sede/servicio/transpor...  2013   
    10  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    11  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    12  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    13  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    14  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    15  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    16  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    17  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    18  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    19  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    20  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    21  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    22  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    23  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    24  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    25  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    26  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    27  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    28  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    29  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    30  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    31  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    32  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    33  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    34  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    35  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    36  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    37  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    38  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    39  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    40  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    41  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    42  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    43  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    44  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    45  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    46  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    47  https://www.zaragoza.es/sede/servicio/transpor...  2014   
    48  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    49  https://www.zaragoza.es/sede/servicio/transpor...  2013   
    
                       type  accidentType           firstAddress  \
    0        SALIDA CALZADA           NaN         COSTA, JOAQUIN   
    1      COLISIÓN ALCANCE           NaN  CADENA(MARQUES DE LA)   
    2      COLISIÓN ALCANCE           NaN   GOMEZ AVELLANEDA, G.   
    3   COLIS FRONTOLATERAL           NaN                 MONZON   
    4        SALIDA CALZADA           NaN                  RIOJA   
    5                 OTRAS           NaN                   MUEL   
    6             ATROPELLO           NaN  PIGNATELLI, RAMON VIA   
    7   CAIDA SOBRE CALZADA           NaN   ALIERTA, AV. CESAREO   
    8   COLIS. MARCHA ATRÁS           NaN         CERBUNA, PEDRO   
    9      COLISIÓN LATERAL           NaN                 ASALTO   
    10                OTRAS           NaN     ARAGON (CORONA DE)   
    11     COLISIÓN ALCANCE           NaN             FRAGUA, LA   
    12       SALIDA CALZADA           NaN   PIRINEOS, AV. DE LOS   
    13     COLISIÓN ALCANCE           NaN  TORRES, CAMINO DE LAS   
    14            ATROPELLO           NaN                  RIOJA   
    15     COLISIÓN ALCANCE           NaN                 ITALIA   
    16     COLISIÓN ALCANCE           NaN   AGUSTIN, PASEO MARIA   
    17     COLISIÓN ALCANCE           NaN   AGUSTIN, PASEO MARIA   
    18     COLISIÓN ALCANCE           NaN   CASPE, AV.COMPROMISO   
    19     COLISIÓN ALCANCE           NaN    MURANO, ISLA DE AV.   
    20     COLISIÓN LATERAL           NaN   HISPANIDAD, RONDA DE   
    21  CAIDA SOBRE CALZADA           NaN      ZARAGOZA LA VIEJA   
    22     COLISIÓN ALCANCE           NaN  ASIN Y PALACIOS, MIG.   
    23  COLIS. MARCHA ATRÁS           NaN   ZAMBRANO, M. (POETA)   
    24       SALIDA CALZADA           NaN  ALBA (DUQUE DE),PASEO   
    25  COLIS FRONTOLATERAL           NaN        HISPANIDAD, VIA   
    26     COLISIÓN LATERAL           NaN    PARAISO, PL.BASILIO   
    27     COLISIÓN LATERAL           NaN   HISPANIDAD, RONDA DE   
    28     COLISIÓN LATERAL           NaN      SAGASTA, PASEO DE   
    29     COLISIÓN LATERAL           NaN    CABALDOS, CAMINO DE   
    30  CAIDA SOBRE CALZADA           NaN  GOYA,FCO.(PINTOR) AV.   
    31     COLISIÓN LATERAL           NaN   AGUSTIN, PASEO MARIA   
    32                OTRAS           NaN                  RIOJA   
    33     COLISIÓN LATERAL           NaN    CONSTITUCION, PASEO   
    34  COLIS. MARCHA ATRÁS           NaN                  TORRE   
    35     COLISIÓN ALCANCE           NaN  ECHEGARAY Y CABALLERO   
    36  COLIS FRONTOLATERAL           NaN    CABALDOS, CAMINO DE   
    37            ATROPELLO           NaN    ALMOZARA, AV. DE LA   
    38  COLIS. MARCHA ATRÁS           NaN      OLIVAN, ALEJANDRO   
    39  COLIS. MARCHA ATRÁS           NaN          ARRUPE, PADRE   
    40  COLIS FRONTOLATERAL           NaN    RUIZ PICASSO, PABLO   
    41            ATROPELLO           NaN       CAMPOAMOR, CLARA   
    42       SALIDA CALZADA           NaN  CASCAJO, CN. DEL  SJN   
    43       SALIDA CALZADA           NaN        EDISON, TOMAS A   
    44     COLISIÓN ALCANCE           NaN      CUELLAR, PASEO DE   
    45     COLISIÓN LATERAL           NaN        HISPANIDAD, VIA   
    46     COLISIÓN ALCANCE           NaN          PLAN, IBON DE   
    47       SALIDA CALZADA           NaN                  FANLO   
    48       SALIDA CALZADA           NaN  AZNAR,ADOLFO(CINEASTA   
    49       SALIDA CALZADA           NaN  ALLENDE, SALVADOR AV.   
    
                secondAddress                                geometry  \
    0            PERAL, ISAAC  -0.8818527060979306,41.649027473051156   
    1                     NaN  -0.8645810716721081,41.661585829868585   
    2      CASTRO, R. (POETA)   -0.887776415002892,41.666992622958105   
    3       GARCIA CONDOY, H.   -0.8825260453930127,41.62957498750602   
    4     NAVARRA, AVENIDA DE     -0.908314757720389,41.6562121210704   
    5                     NaN   -0.8691088511672924,41.65949772773082   
    6                     NaN  -0.8880337913721866,41.633353667694024   
    7              AULA, LUIS    -0.8708838775078237,41.6390382112928   
    8                     NaN   -0.8970649943808023,41.64083344974765   
    9            COCCI, JORGE   -0.8718525605769747,41.64904657717317   
    10   SAN ANTONIO M CLARET   -0.8964627561577849,41.64322365075108   
    11        GASSIER, PIERRE   -0.8778095796207178,41.68753087470739   
    12                    NaN  -0.8812157329722801,41.661646612715046   
    13                    NaN    -0.8762000299022707,41.6454384961757   
    14    NAVARRA, AVENIDA DE   -0.9089013552408617,41.65543768899759   
    15                    NaN   -0.9004729973337304,41.65180346604993   
    16     MAYANDIA (GENERAL)   -0.8917562993466011,41.65233828238132   
    17              SANTA ANA    -0.888856043735591,41.65040494617356   
    18                    NaN  -0.8629911318784169,41.645335650478316   
    19                    NaN  -0.8870207060655807,41.609992514227066   
    20   ALIERTA, AV. CESAREO   -0.8636325074780108,41.63379905763323   
    21                    NaN   -0.8760724207544668,41.63275556609146   
    22                    NaN   -0.9036852209830768,41.63808926467497   
    23                    NaN  -0.8896980442453839,41.677487884305975   
    24                    NaN  -0.9018264648858587,41.620591734015946   
    25     MADRID, AVENIDA DE   -0.9187726932212442,41.64931371437485   
    26                    NaN  -0.8855988456901538,41.646890443474554   
    27                    NaN    -0.887523212911549,41.62404668544956   
    28                    NaN   -0.8863120908790753,41.63964884250951   
    29                    NaN  -0.8689640327130923,41.638477534601776   
    30   TORRES MORALES, M.G.   -0.8900650666830714,41.64332496247496   
    31                    NaN   -0.8918524618079099,41.65260977469196   
    32                    NaN   -0.9104038365599549,41.65248328671194   
    33    PARAISO, PL.BASILIO    -0.8850103896969528,41.6474034449745   
    34                    NaN   -0.8734135018983006,41.64926981833846   
    35  MATUTE HERVIAS,JULIAN  -0.8593239531218387,41.650740541708075   
    36       CASTELAR, EMILIO   -0.868891092151338,41.638807389014836   
    37  PUERTA DE SANCHO, AV.   -0.9008107424460443,41.66374540604866   
    38  BOSQUED, JOSE (MOSEN)   -0.9211220937948997,41.64886535549928   
    39       VAZQUEZ DE MELLA   -0.9026681648170423,41.63265453864093   
    40   ZAMBRANO, M. (POETA)   -0.8893162332922886,41.67281318904247   
    41                    NaN   -0.8890866503471749,41.66895757951277   
    42                    NaN   -0.8439506345833918,41.71496486522088   
    43                    NaN   -0.8665477541801948,41.67007665525934   
    44                    NaN   -0.8848493117953854,41.63484525009101   
    45  GOMEZ LAGUNA(ALCALDE)   -0.9147014503640727,41.64060309287472   
    46  AEROPUERTO, CARRETERA   -0.9388159722509236,41.66210291413718   
    47                    NaN   -0.9157439755527074,41.63348367532985   
    48  BELTRAN,J.M.(CINEASTA   -0.8869959298557372,41.67593597602368   
    49                    NaN   -0.876909940066992,41.672106692157605   
    
                                                   reason    area  \
    0           PERDIDA del control por FALTA de ATENCIÓN     NaN   
    1                 DISTANCIA DE SEGURIDAD, no mantener  2560.0   
    2           PERDIDA del control por FALTA de ATENCIÓN  2598.0   
    3         CEDA EL PASO, no respetar prioridad de paso  2555.0   
    4        PERDIDA del control por VELOCIDAD INADECUADA  2554.0   
    5             Caída de ocupante en Transporte Público  2578.0   
    6         PEATÓN cruza calz SIN PREFER. fuera de paso  2606.0   
    7   INVADIR otro carril en el mismo sentido de cir...  2583.0   
    8           PERDIDA del control por FALTA de ATENCIÓN  2556.0   
    9   INVADIR otro carril en el mismo sentido de cir...  4657.0   
    10            Caída de ocupante en Transporte Público    63.0   
    11          PERDIDA del control por FALTA de ATENCIÓN  4780.0   
    12          PERDIDA del control por FALTA de ATENCIÓN  4661.0   
    13          PERDIDA del control por FALTA de ATENCIÓN  4667.0   
    14  PEATÓN cruza calz SIN PREFER. en PASO CON semá...  4664.0   
    15          PERDIDA del control por FALTA de ATENCIÓN  4671.0   
    16                DISTANCIA DE SEGURIDAD, no mantener    18.0   
    17          PERDIDA del control por FALTA de ATENCIÓN  4718.0   
    18          PERDIDA del control por FALTA de ATENCIÓN  4723.0   
    19          PERDIDA del control por FALTA de ATENCIÓN     NaN   
    20                     PUERTA abierta incorrectamente    17.0   
    21          PERDIDA del control por FALTA de ATENCIÓN  4677.0   
    22          PERDIDA del control por FALTA de ATENCIÓN     NaN   
    23                                       MARCHA ATRÁS  4783.0   
    24       PERDIDA del control por VELOCIDAD INADECUADA  4679.0   
    25            SEMÁFORO, no respetar prioridad de paso  4773.0   
    26  INVADIR otro carril en el mismo sentido de cir...  4702.0   
    27                     PUERTA abierta incorrectamente  4701.0   
    28  INVADIR otro carril en el mismo sentido de cir...  4700.0   
    29  INVADIR otro carril en el mismo sentido de cir...  4752.0   
    30                DISTANCIA DE SEGURIDAD, no mantener  4751.0   
    31  INVADIR otro carril en el mismo sentido de cir...  4750.0   
    32                                       OTRAS CAUSAS     NaN   
    33  INVADIR otro carril en el mismo sentido de cir...  2682.0   
    34                                       MARCHA ATRÁS  2626.0   
    35          PERDIDA del control por FALTA de ATENCIÓN  2605.0   
    36  INVADIR otro carril en el mismo sentido de cir...  2591.0   
    37  PEATÓN cruza calz CON PREFER. en PASO  CON sem...  2610.0   
    38                                       MARCHA ATRÁS  2594.0   
    39                                       MARCHA ATRÁS  2596.0   
    40                                       OTRAS CAUSAS  2640.0   
    41  PEATÓN cruza calz CON PREFER. en PASO  SIN sem...  2600.0   
    42          PERDIDA del control por FALTA de ATENCIÓN     NaN   
    43          PERDIDA del control por FALTA de ATENCIÓN     NaN   
    44          PERDIDA del control por FALTA de ATENCIÓN  2604.0   
    45  INVADIR otro carril en el mismo sentido de cir...  2624.0   
    46                DISTANCIA DE SEGURIDAD, no mantener  2611.0   
    47          PERDIDA del control por FALTA de ATENCIÓN  2631.0   
    48          PERDIDA del control por FALTA de ATENCIÓN  4438.0   
    49          PERDIDA del control por FALTA de ATENCIÓN  4684.0   
    
                creationDate  daniosMateriales  falloMecanico estadoPavimento  \
    0   2014-10-09T00:00:00Z              True          False     BUEN ESTADO   
    1   2014-10-23T00:00:00Z             False          False     BUEN ESTADO   
    2   2014-10-23T00:00:00Z             False          False     BUEN ESTADO   
    3   2014-10-23T00:00:00Z             False          False     BUEN ESTADO   
    4   2014-10-24T00:00:00Z             False          False     BUEN ESTADO   
    5   2014-10-24T00:00:00Z             False          False     BUEN ESTADO   
    6   2014-10-24T00:00:00Z             False          False     BUEN ESTADO   
    7   2014-10-24T00:00:00Z             False          False     BUEN ESTADO   
    8   2014-10-24T00:00:00Z              True          False     BUEN ESTADO   
    9   2013-12-20T00:00:00Z             False          False     BUEN ESTADO   
    10  2013-12-21T00:00:00Z             False          False     BUEN ESTADO   
    11  2013-12-22T00:00:00Z              True          False     BUEN ESTADO   
    12  2013-12-22T00:00:00Z             False          False     BUEN ESTADO   
    13  2013-12-22T00:00:00Z             False          False     BUEN ESTADO   
    14  2013-12-22T00:00:00Z             False          False     BUEN ESTADO   
    15  2013-12-22T00:00:00Z              True          False     BUEN ESTADO   
    16  2013-12-20T00:00:00Z             False          False     BUEN ESTADO   
    17  2013-12-23T00:00:00Z             False          False     BUEN ESTADO   
    18  2013-12-23T00:00:00Z             False          False     BUEN ESTADO   
    19  2013-12-23T00:00:00Z              True          False     BUEN ESTADO   
    20  2013-12-23T00:00:00Z             False          False     BUEN ESTADO   
    21  2013-12-21T00:00:00Z             False          False     BUEN ESTADO   
    22  2013-12-17T00:00:00Z              True          False     BUEN ESTADO   
    23  2013-12-23T00:00:00Z              True          False     BUEN ESTADO   
    24  2013-12-15T00:00:00Z              True          False     BUEN ESTADO   
    25  2013-12-20T00:00:00Z              True          False     BUEN ESTADO   
    26  2013-12-17T00:00:00Z              True          False     BUEN ESTADO   
    27  2013-12-20T00:00:00Z              True          False     BUEN ESTADO   
    28  2013-12-19T00:00:00Z              True          False     BUEN ESTADO   
    29  2013-12-24T00:00:00Z             False          False     BUEN ESTADO   
    30  2013-12-24T00:00:00Z             False          False     BUEN ESTADO   
    31  2013-12-25T00:00:00Z             False          False     BUEN ESTADO   
    32  2013-12-19T00:00:00Z              True          False     BUEN ESTADO   
    33  2014-10-24T00:00:00Z              True          False     BUEN ESTADO   
    34  2014-10-27T00:00:00Z              True          False     BUEN ESTADO   
    35  2014-10-27T00:00:00Z              True          False     BUEN ESTADO   
    36  2014-10-25T00:00:00Z              True          False     BUEN ESTADO   
    37  2014-10-29T00:00:00Z             False          False     BUEN ESTADO   
    38  2014-10-24T00:00:00Z              True          False     BUEN ESTADO   
    39  2014-10-20T00:00:00Z              True          False     BUEN ESTADO   
    40  2014-10-29T00:00:00Z             False          False     BUEN ESTADO   
    41  2014-10-29T00:00:00Z             False          False     BUEN ESTADO   
    42  2014-10-29T00:00:00Z             False          False     BUEN ESTADO   
    43  2014-10-29T00:00:00Z              True          False     BUEN ESTADO   
    44  2014-10-28T00:00:00Z              True          False     BUEN ESTADO   
    45  2014-10-29T00:00:00Z              True          False     BUEN ESTADO   
    46  2014-10-27T00:00:00Z              True          False     BUEN ESTADO   
    47  2014-10-27T00:00:00Z              True          False     BUEN ESTADO   
    48  2013-12-02T00:00:00Z              True          False     BUEN ESTADO   
    49  2013-12-05T00:00:00Z              True          False     BUEN ESTADO   
    
        tipoEstadoPavimento estadoAtmosfera  tipoEstadoAtmosfera  \
    0                   NaN     BUEN ESTADO                  NaN   
    1                   NaN     BUEN ESTADO                  NaN   
    2                   NaN     BUEN ESTADO                  NaN   
    3                   NaN     BUEN ESTADO                  NaN   
    4                   NaN     BUEN ESTADO                  NaN   
    5                   NaN     BUEN ESTADO                  NaN   
    6                   NaN     BUEN ESTADO                  NaN   
    7                   NaN     BUEN ESTADO                  NaN   
    8                   NaN     BUEN ESTADO                  NaN   
    9                   NaN     BUEN ESTADO                  NaN   
    10                  NaN     BUEN ESTADO                  NaN   
    11                  NaN     BUEN ESTADO                  NaN   
    12                  NaN     BUEN ESTADO                  NaN   
    13                  NaN     BUEN ESTADO                  NaN   
    14                  NaN     BUEN ESTADO                  NaN   
    15                  NaN     BUEN ESTADO                  NaN   
    16                  NaN     BUEN ESTADO                  NaN   
    17                  NaN     BUEN ESTADO                  NaN   
    18                  NaN     BUEN ESTADO                  NaN   
    19                  NaN     BUEN ESTADO                  NaN   
    20                  NaN     BUEN ESTADO                  NaN   
    21                  NaN     BUEN ESTADO                  NaN   
    22                  NaN     BUEN ESTADO                  NaN   
    23                  NaN     BUEN ESTADO                  NaN   
    24                  NaN     BUEN ESTADO                  NaN   
    25                  NaN     BUEN ESTADO                  NaN   
    26                  NaN     BUEN ESTADO                  NaN   
    27                  NaN     BUEN ESTADO                  NaN   
    28                  NaN     BUEN ESTADO                  NaN   
    29                  NaN     BUEN ESTADO                  NaN   
    30                  NaN     BUEN ESTADO                  NaN   
    31                  NaN     BUEN ESTADO                  NaN   
    32                  NaN     BUEN ESTADO                  NaN   
    33                  NaN     BUEN ESTADO                  NaN   
    34                  NaN     BUEN ESTADO                  NaN   
    35                  NaN     BUEN ESTADO                  NaN   
    36                  NaN     BUEN ESTADO                  NaN   
    37                  NaN     BUEN ESTADO                  NaN   
    38                  NaN     BUEN ESTADO                  NaN   
    39                  NaN     BUEN ESTADO                  NaN   
    40                  NaN     BUEN ESTADO                  NaN   
    41                  NaN     BUEN ESTADO                  NaN   
    42                  NaN     BUEN ESTADO                  NaN   
    43                  NaN     BUEN ESTADO                  NaN   
    44                  NaN     BUEN ESTADO                  NaN   
    45                  NaN     BUEN ESTADO                  NaN   
    46                  NaN     BUEN ESTADO                  NaN   
    47                  NaN     BUEN ESTADO                  NaN   
    48                  NaN     BUEN ESTADO                  NaN   
    49                  NaN     BUEN ESTADO                  NaN   
    
                                                 afectado  \
    0                                                 NaN   
    1   https://www.zaragoza.es/sede/servicio/transpor...   
    2   https://www.zaragoza.es/sede/servicio/transpor...   
    3   https://www.zaragoza.es/sede/servicio/transpor...   
    4   https://www.zaragoza.es/sede/servicio/transpor...   
    5   https://www.zaragoza.es/sede/servicio/transpor...   
    6   https://www.zaragoza.es/sede/servicio/transpor...   
    7   https://www.zaragoza.es/sede/servicio/transpor...   
    8                                                 NaN   
    9   https://www.zaragoza.es/sede/servicio/transpor...   
    10  https://www.zaragoza.es/sede/servicio/transpor...   
    11                                                NaN   
    12  https://www.zaragoza.es/sede/servicio/transpor...   
    13  https://www.zaragoza.es/sede/servicio/transpor...   
    14  https://www.zaragoza.es/sede/servicio/transpor...   
    15                                                NaN   
    16  https://www.zaragoza.es/sede/servicio/transpor...   
    17  https://www.zaragoza.es/sede/servicio/transpor...   
    18  https://www.zaragoza.es/sede/servicio/transpor...   
    19                                                NaN   
    20  https://www.zaragoza.es/sede/servicio/transpor...   
    21  https://www.zaragoza.es/sede/servicio/transpor...   
    22                                                NaN   
    23                                                NaN   
    24                                                NaN   
    25                                                NaN   
    26                                                NaN   
    27                                                NaN   
    28                                                NaN   
    29  https://www.zaragoza.es/sede/servicio/transpor...   
    30  https://www.zaragoza.es/sede/servicio/transpor...   
    31  https://www.zaragoza.es/sede/servicio/transpor...   
    32                                                NaN   
    33                                                NaN   
    34                                                NaN   
    35                                                NaN   
    36                                                NaN   
    37  https://www.zaragoza.es/sede/servicio/transpor...   
    38                                                NaN   
    39                                                NaN   
    40  https://www.zaragoza.es/sede/servicio/transpor...   
    41  https://www.zaragoza.es/sede/servicio/transpor...   
    42  https://www.zaragoza.es/sede/servicio/transpor...   
    43                                                NaN   
    44                                                NaN   
    45                                                NaN   
    46                                                NaN   
    47                                                NaN   
    48                                                NaN   
    49                                                NaN   
    
                                                 vehiculo  
    0   https://www.zaragoza.es/sede/servicio/transpor...  
    1   https://www.zaragoza.es/sede/servicio/transpor...  
    2   https://www.zaragoza.es/sede/servicio/transpor...  
    3   https://www.zaragoza.es/sede/servicio/transpor...  
    4   https://www.zaragoza.es/sede/servicio/transpor...  
    5   https://www.zaragoza.es/sede/servicio/transpor...  
    6   https://www.zaragoza.es/sede/servicio/transpor...  
    7   https://www.zaragoza.es/sede/servicio/transpor...  
    8   https://www.zaragoza.es/sede/servicio/transpor...  
    9   https://www.zaragoza.es/sede/servicio/transpor...  
    10  https://www.zaragoza.es/sede/servicio/transpor...  
    11  https://www.zaragoza.es/sede/servicio/transpor...  
    12  https://www.zaragoza.es/sede/servicio/transpor...  
    13  https://www.zaragoza.es/sede/servicio/transpor...  
    14  https://www.zaragoza.es/sede/servicio/transpor...  
    15  https://www.zaragoza.es/sede/servicio/transpor...  
    16  https://www.zaragoza.es/sede/servicio/transpor...  
    17  https://www.zaragoza.es/sede/servicio/transpor...  
    18  https://www.zaragoza.es/sede/servicio/transpor...  
    19  https://www.zaragoza.es/sede/servicio/transpor...  
    20  https://www.zaragoza.es/sede/servicio/transpor...  
    21  https://www.zaragoza.es/sede/servicio/transpor...  
    22  https://www.zaragoza.es/sede/servicio/transpor...  
    23  https://www.zaragoza.es/sede/servicio/transpor...  
    24  https://www.zaragoza.es/sede/servicio/transpor...  
    25  https://www.zaragoza.es/sede/servicio/transpor...  
    26  https://www.zaragoza.es/sede/servicio/transpor...  
    27  https://www.zaragoza.es/sede/servicio/transpor...  
    28  https://www.zaragoza.es/sede/servicio/transpor...  
    29  https://www.zaragoza.es/sede/servicio/transpor...  
    30  https://www.zaragoza.es/sede/servicio/transpor...  
    31  https://www.zaragoza.es/sede/servicio/transpor...  
    32  https://www.zaragoza.es/sede/servicio/transpor...  
    33  https://www.zaragoza.es/sede/servicio/transpor...  
    34  https://www.zaragoza.es/sede/servicio/transpor...  
    35  https://www.zaragoza.es/sede/servicio/transpor...  
    36  https://www.zaragoza.es/sede/servicio/transpor...  
    37  https://www.zaragoza.es/sede/servicio/transpor...  
    38  https://www.zaragoza.es/sede/servicio/transpor...  
    39  https://www.zaragoza.es/sede/servicio/transpor...  
    40  https://www.zaragoza.es/sede/servicio/transpor...  
    41  https://www.zaragoza.es/sede/servicio/transpor...  
    42  https://www.zaragoza.es/sede/servicio/transpor...  
    43  https://www.zaragoza.es/sede/servicio/transpor...  
    44  https://www.zaragoza.es/sede/servicio/transpor...  
    45  https://www.zaragoza.es/sede/servicio/transpor...  
    46  https://www.zaragoza.es/sede/servicio/transpor...  
    47  https://www.zaragoza.es/sede/servicio/transpor...  
    48  https://www.zaragoza.es/sede/servicio/transpor...  
    49  https://www.zaragoza.es/sede/servicio/transpor...  >



Esto es un resumen de los datos de la tabla. `.info` nos informa sobre el conjunto de datos que estamos tratando. Estos son sobre la naturaleza de una serie de accidentes de tráfico: año, motivo, dirección... A continuación queremos conocer la razón de cada accidente de tráfico, para lo que ponemos `['reason]` detrás de *df_zrgz*. No lleva `.` porque no se trata de una función sobre los datos sino una forma de visualización diferente en la que nosotros pedimos el dato que queremos que nos muestre. La sisntaxis es `df['categoría']`, en este caso el motivo del accidente.


```python
df_zrgz['reason']
```




    0             PERDIDA del control por FALTA de ATENCIÓN
    1                   DISTANCIA DE SEGURIDAD, no mantener
    2             PERDIDA del control por FALTA de ATENCIÓN
    3           CEDA EL PASO, no respetar prioridad de paso
    4          PERDIDA del control por VELOCIDAD INADECUADA
    5               Caída de ocupante en Transporte Público
    6           PEATÓN cruza calz SIN PREFER. fuera de paso
    7     INVADIR otro carril en el mismo sentido de cir...
    8             PERDIDA del control por FALTA de ATENCIÓN
    9     INVADIR otro carril en el mismo sentido de cir...
    10              Caída de ocupante en Transporte Público
    11            PERDIDA del control por FALTA de ATENCIÓN
    12            PERDIDA del control por FALTA de ATENCIÓN
    13            PERDIDA del control por FALTA de ATENCIÓN
    14    PEATÓN cruza calz SIN PREFER. en PASO CON semá...
    15            PERDIDA del control por FALTA de ATENCIÓN
    16                  DISTANCIA DE SEGURIDAD, no mantener
    17            PERDIDA del control por FALTA de ATENCIÓN
    18            PERDIDA del control por FALTA de ATENCIÓN
    19            PERDIDA del control por FALTA de ATENCIÓN
    20                       PUERTA abierta incorrectamente
    21            PERDIDA del control por FALTA de ATENCIÓN
    22            PERDIDA del control por FALTA de ATENCIÓN
    23                                         MARCHA ATRÁS
    24         PERDIDA del control por VELOCIDAD INADECUADA
    25              SEMÁFORO, no respetar prioridad de paso
    26    INVADIR otro carril en el mismo sentido de cir...
    27                       PUERTA abierta incorrectamente
    28    INVADIR otro carril en el mismo sentido de cir...
    29    INVADIR otro carril en el mismo sentido de cir...
    30                  DISTANCIA DE SEGURIDAD, no mantener
    31    INVADIR otro carril en el mismo sentido de cir...
    32                                         OTRAS CAUSAS
    33    INVADIR otro carril en el mismo sentido de cir...
    34                                         MARCHA ATRÁS
    35            PERDIDA del control por FALTA de ATENCIÓN
    36    INVADIR otro carril en el mismo sentido de cir...
    37    PEATÓN cruza calz CON PREFER. en PASO  CON sem...
    38                                         MARCHA ATRÁS
    39                                         MARCHA ATRÁS
    40                                         OTRAS CAUSAS
    41    PEATÓN cruza calz CON PREFER. en PASO  SIN sem...
    42            PERDIDA del control por FALTA de ATENCIÓN
    43            PERDIDA del control por FALTA de ATENCIÓN
    44            PERDIDA del control por FALTA de ATENCIÓN
    45    INVADIR otro carril en el mismo sentido de cir...
    46                  DISTANCIA DE SEGURIDAD, no mantener
    47            PERDIDA del control por FALTA de ATENCIÓN
    48            PERDIDA del control por FALTA de ATENCIÓN
    49            PERDIDA del control por FALTA de ATENCIÓN
    Name: reason, dtype: object



Si queremos ver el conjunto de los datos (en este caso razones de los dintintos accidentes) sin una distinción por filas o el número de cada uno de los accidentes recogidos en la base de datos utilizamos la función `unique()`.


```python
df_zrgz['reason'].unique()
```




    array(['PERDIDA del control por FALTA de ATENCIÓN',
           'DISTANCIA DE SEGURIDAD, no mantener',
           'CEDA EL PASO, no respetar prioridad de paso',
           'PERDIDA del control por VELOCIDAD INADECUADA',
           'Caída de ocupante en Transporte Público',
           'PEATÓN cruza calz SIN PREFER. fuera de paso',
           'INVADIR otro carril en el mismo sentido de circulación',
           'PEATÓN cruza calz SIN PREFER. en PASO CON semáforo',
           'PUERTA abierta incorrectamente', 'MARCHA ATRÁS',
           'SEMÁFORO, no respetar prioridad de paso', 'OTRAS CAUSAS',
           'PEATÓN cruza calz CON PREFER. en PASO  CON semáforo',
           'PEATÓN cruza calz CON PREFER. en PASO  SIN semáforo'],
          dtype=object)



La función `.unique()` sirve para delimitar los valores únicos en columnas. Es decir, las razones (categoría *reason* que elegimos visualizar antes) de los motivos del accidente que no se repiten en este conjunto de datos. Con la sintaxis descrita anteriormente cambiamos la categoría que queremos que nos muestre para acercarnos más a los datos e ir extrayendo toda su información.


```python
df_zrgz['type'].unique()
```




    array(['SALIDA CALZADA', 'COLISIÓN ALCANCE', 'COLIS FRONTOLATERAL',
           'OTRAS', 'ATROPELLO', 'CAIDA SOBRE CALZADA', 'COLIS. MARCHA ATRÁS',
           'COLISIÓN LATERAL'], dtype=object)



Tras explorar los datos los representamos en el mapa.

## Representación en el mapa

Pedimos que nos enseñe los datos de las coordenadas geográficas a representar en el mapa que son los que se encuentran en la categoría *geometry*.


```python
df_zrgz['geometry']
```




    0     -0.8818527060979306,41.649027473051156
    1     -0.8645810716721081,41.661585829868585
    2      -0.887776415002892,41.666992622958105
    3      -0.8825260453930127,41.62957498750602
    4        -0.908314757720389,41.6562121210704
    5      -0.8691088511672924,41.65949772773082
    6     -0.8880337913721866,41.633353667694024
    7       -0.8708838775078237,41.6390382112928
    8      -0.8970649943808023,41.64083344974765
    9      -0.8718525605769747,41.64904657717317
    10     -0.8964627561577849,41.64322365075108
    11     -0.8778095796207178,41.68753087470739
    12    -0.8812157329722801,41.661646612715046
    13      -0.8762000299022707,41.6454384961757
    14     -0.9089013552408617,41.65543768899759
    15     -0.9004729973337304,41.65180346604993
    16     -0.8917562993466011,41.65233828238132
    17      -0.888856043735591,41.65040494617356
    18    -0.8629911318784169,41.645335650478316
    19    -0.8870207060655807,41.609992514227066
    20     -0.8636325074780108,41.63379905763323
    21     -0.8760724207544668,41.63275556609146
    22     -0.9036852209830768,41.63808926467497
    23    -0.8896980442453839,41.677487884305975
    24    -0.9018264648858587,41.620591734015946
    25     -0.9187726932212442,41.64931371437485
    26    -0.8855988456901538,41.646890443474554
    27      -0.887523212911549,41.62404668544956
    28     -0.8863120908790753,41.63964884250951
    29    -0.8689640327130923,41.638477534601776
    30     -0.8900650666830714,41.64332496247496
    31     -0.8918524618079099,41.65260977469196
    32     -0.9104038365599549,41.65248328671194
    33      -0.8850103896969528,41.6474034449745
    34     -0.8734135018983006,41.64926981833846
    35    -0.8593239531218387,41.650740541708075
    36     -0.868891092151338,41.638807389014836
    37     -0.9008107424460443,41.66374540604866
    38     -0.9211220937948997,41.64886535549928
    39     -0.9026681648170423,41.63265453864093
    40     -0.8893162332922886,41.67281318904247
    41     -0.8890866503471749,41.66895757951277
    42     -0.8439506345833918,41.71496486522088
    43     -0.8665477541801948,41.67007665525934
    44     -0.8848493117953854,41.63484525009101
    45     -0.9147014503640727,41.64060309287472
    46     -0.9388159722509236,41.66210291413718
    47     -0.9157439755527074,41.63348367532985
    48     -0.8869959298557372,41.67593597602368
    49     -0.876909940066992,41.672106692157605
    Name: geometry, dtype: object



Le pedimos que nos enseñe el nombre de dichas coordenadas para tenerlas a mano para poder escribir su nombre en el mapa. La categoría es *firstAddress*. Añado la función `.unique()` para acortar su extensión. Esto no podía realizarlo en la función anterior porque trabajaba con números y era necesaria la distinción por líneas de cada una de las coordenadas para poder diferenciarlas. Pero ahora puedo prescindir de ello ya que trabajo con texto. 


```python
df_zrgz['firstAddress'].unique()
```




    array(['COSTA, JOAQUIN', 'CADENA(MARQUES DE LA)', 'GOMEZ AVELLANEDA, G.',
           'MONZON', 'RIOJA', 'MUEL', 'PIGNATELLI, RAMON VIA',
           'ALIERTA, AV. CESAREO', 'CERBUNA, PEDRO', 'ASALTO',
           'ARAGON (CORONA DE)', 'FRAGUA, LA', 'PIRINEOS, AV. DE LOS',
           'TORRES, CAMINO DE LAS', 'ITALIA', 'AGUSTIN, PASEO MARIA',
           'CASPE, AV.COMPROMISO', 'MURANO, ISLA DE AV.',
           'HISPANIDAD, RONDA DE', 'ZARAGOZA LA VIEJA',
           'ASIN Y PALACIOS, MIG.', 'ZAMBRANO, M. (POETA)',
           'ALBA (DUQUE DE),PASEO', 'HISPANIDAD, VIA', 'PARAISO, PL.BASILIO',
           'SAGASTA, PASEO DE', 'CABALDOS, CAMINO DE',
           'GOYA,FCO.(PINTOR) AV.', 'CONSTITUCION, PASEO', 'TORRE',
           'ECHEGARAY Y CABALLERO', 'ALMOZARA, AV. DE LA',
           'OLIVAN, ALEJANDRO', 'ARRUPE, PADRE', 'RUIZ PICASSO, PABLO',
           'CAMPOAMOR, CLARA', 'CASCAJO, CN. DEL  SJN', 'EDISON, TOMAS A',
           'CUELLAR, PASEO DE', 'PLAN, IBON DE', 'FANLO',
           'AZNAR,ADOLFO(CINEASTA', 'ALLENDE, SALVADOR AV.'], dtype=object)



Creamos un mapa (m) a partir del anterior al que añadimos marcardores con las coordenadas y nombres de las calles correspondientes utilizando la función `folium.Marquer`.

La sintaxis de la función `folium.map`es la siguiente: 
- (`location=`*coordenadas de referencia*`,`
- `zoom_start=`*número pertinente al caso*`,`
- `tiles=`*estilo de mapa que queramos*). 

En este caso he borrado la opción 'tiles' opción ya que tras probar distintos estilos como 'Stamen Terrain' o 'Stamen Toner' he preferido el que viene definido en Folium y por tanto no necesita ser especificado.  

La sintaxis de `folium.Marker`, que forma parte de nuestro nuevo mapa "m", es la siguiente:
- `([*coordenadas],`
- `popup=`*nombre de la calle*`,`
- `tooltip=`*lo que quiera que se vea al posicionar el cursor en el marcador*`)` Puedo definir esta variable con antelación para dejarla preestablecida si quiero poner en todas las localizaciones la misma etiqueta; 'accidente' en este caso. La sintaxis entonces es para todos los marcadores `tooltip=tooltip)`
- `.add_to(m)` para añadir los cambios al nuevo mapa resultante. 

Lo he llevado a cabo con las dos primeras coordenadas como ejemplo pero el proceso es el mismo para todas. 


```python
m=folium.Map(location=geo_zrgz,zoom_start=13)
tooltip='Accidente'
folium.Marker([-0.8818527060979306,41.649027473051156], popup='Calle Joaquín Costa', tooltip=tooltip).add_to(m)
folium.Marker([-0.8645810716721081,41.661585829868585], popup='Calle Marqués de la Cadena', tooltip=tooltip).add_to(m)
m
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe srcdoc="&lt;!DOCTYPE html&gt;
&lt;head&gt;    
    &lt;meta http-equiv=&quot;content-type&quot; content=&quot;text/html; charset=UTF-8&quot; /&gt;

        &lt;script&gt;
            L_NO_TOUCH = false;
            L_DISABLE_3D = false;
        &lt;/script&gt;

    &lt;style&gt;html, body {width: 100%;height: 100%;margin: 0;padding: 0;}&lt;/style&gt;
    &lt;style&gt;#map {position:absolute;top:0;bottom:0;right:0;left:0;}&lt;/style&gt;
    &lt;script src=&quot;https://cdn.jsdelivr.net/npm/leaflet@1.6.0/dist/leaflet.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;https://code.jquery.com/jquery-1.12.4.min.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;https://cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js&quot;&gt;&lt;/script&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://cdn.jsdelivr.net/npm/leaflet@1.6.0/dist/leaflet.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css&quot;/&gt;

            &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width,
                initial-scale=1.0, maximum-scale=1.0, user-scalable=no&quot; /&gt;
            &lt;style&gt;
                #map_f3b54300ec57ac58075b6780fbc340d3 {
                    position: relative;
                    width: 100.0%;
                    height: 100.0%;
                    left: 0.0%;
                    top: 0.0%;
                }
            &lt;/style&gt;

&lt;/head&gt;
&lt;body&gt;    

            &lt;div class=&quot;folium-map&quot; id=&quot;map_f3b54300ec57ac58075b6780fbc340d3&quot; &gt;&lt;/div&gt;

&lt;/body&gt;
&lt;script&gt;    

            var map_f3b54300ec57ac58075b6780fbc340d3 = L.map(
                &quot;map_f3b54300ec57ac58075b6780fbc340d3&quot;,
                {
                    center: [41.646693, -0.887712],
                    crs: L.CRS.EPSG3857,
                    zoom: 13,
                    zoomControl: true,
                    preferCanvas: false,
                }
            );





            var tile_layer_ce444db553ec56391f02c4c99224916b = L.tileLayer(
                &quot;https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png&quot;,
                {&quot;attribution&quot;: &quot;Data by \u0026copy; \u003ca href=\&quot;http://openstreetmap.org\&quot;\u003eOpenStreetMap\u003c/a\u003e, under \u003ca href=\&quot;http://www.openstreetmap.org/copyright\&quot;\u003eODbL\u003c/a\u003e.&quot;, &quot;detectRetina&quot;: false, &quot;maxNativeZoom&quot;: 18, &quot;maxZoom&quot;: 18, &quot;minZoom&quot;: 0, &quot;noWrap&quot;: false, &quot;opacity&quot;: 1, &quot;subdomains&quot;: &quot;abc&quot;, &quot;tms&quot;: false}
            ).addTo(map_f3b54300ec57ac58075b6780fbc340d3);


            var marker_b895d69ed23970100aaf397ae3cc8e41 = L.marker(
                [-0.8818527060979306, 41.649027473051156],
                {}
            ).addTo(map_f3b54300ec57ac58075b6780fbc340d3);


        var popup_d4f99a1d40297c5dcf500c65e88f6f9c = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_2e1c429d071967516427ed5c3501d3d4 = $(`&lt;div id=&quot;html_2e1c429d071967516427ed5c3501d3d4&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Calle Joaquín Costa&lt;/div&gt;`)[0];
            popup_d4f99a1d40297c5dcf500c65e88f6f9c.setContent(html_2e1c429d071967516427ed5c3501d3d4);


        marker_b895d69ed23970100aaf397ae3cc8e41.bindPopup(popup_d4f99a1d40297c5dcf500c65e88f6f9c)
        ;




            marker_b895d69ed23970100aaf397ae3cc8e41.bindTooltip(
                `&lt;div&gt;
                     Accidente
                 &lt;/div&gt;`,
                {&quot;sticky&quot;: true}
            );


            var marker_7f8d4b3fafb25a0650d7d602ebcea836 = L.marker(
                [-0.8645810716721081, 41.661585829868585],
                {}
            ).addTo(map_f3b54300ec57ac58075b6780fbc340d3);


        var popup_8410986b3c5786599dbadda589eac505 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_dc74d5c5937f07f61321a0385ba9d88f = $(`&lt;div id=&quot;html_dc74d5c5937f07f61321a0385ba9d88f&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Calle Marqués de la Cadena&lt;/div&gt;`)[0];
            popup_8410986b3c5786599dbadda589eac505.setContent(html_dc74d5c5937f07f61321a0385ba9d88f);


        marker_7f8d4b3fafb25a0650d7d602ebcea836.bindPopup(popup_8410986b3c5786599dbadda589eac505)
        ;




            marker_7f8d4b3fafb25a0650d7d602ebcea836.bindTooltip(
                `&lt;div&gt;
                     Accidente
                 &lt;/div&gt;`,
                {&quot;sticky&quot;: true}
            );

&lt;/script&gt;" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



Vemos así los puntos de los accidentes marcados en el mapa. 
