# Práctica 4 

La práctica 4 supone la realización de un cuaderno en Jupyter con **Phyton**. En él se explora, analiza y representan un conjunto de datos abiertos en formato **CSV** de información epidemiológica. Se trata de los **casos confirmados y tasas de incidencia acumulada (TIA) para población de 60 y más años de edad del municipio de Alcobendas** desde el inicio de la pandemia (25 de marzo de 2020) hasta el pasado 29 de marzo. La fuente de los datos es la Red de Vigilancia Epidemiológica de la Comunidad de Madrid y la información presentada es resultado de la implantación de la nueva Estrategia de vigilancia y control frente a la COVID-19 tras la fase aguda de la pandemia. Se puede acceder a los datos desde [aquí](https://datos.gob.es/es/catalogo/l01280066-covid-19-poblacion-de-mas-de-60-anos-municipio-de-alcobendas).

Este cuaderno trabaja con las librerías **Pandas** y **Folium** para la representación gráfica de los datos y la visualización de un mapa. Tras la preparación de la librería (Pandas en este caso), definición de la variable y creación del dataframe se procede a la exploración del mismo con distintas funciones como `df.describe()` o ´df['columna']´ entre otras. A continuación se combinan tipos de datos diferentes con la función ´df.set_index()[]´ que posteriormente quedan representados en un gráfico con ´plot()´. Con la librería *Folium* las 5 zonas sanitarias de Alcobendas quedan visualizadas y marcadas en un mapa. Todo el proceso queda documentado explícitamente en lenduaje markdown. Por último, partiendo del análisis y representación de los datos relizada, se bosqueja una historia con los mismos. Guardamos los datos (**.csv**), un gráfico con la representación de los casos totales (**.png**), y el mapa con la visualización de las 5 zonas sanitarias de Alcobendas (**.html**).

Se puede encontrar el cuaderno en dos formatos: ***.html*** y ***.ipnyb***. Por lo que esta práctica consta de los siguientes archivos: 
- [P-4.Datos](practica-4.csv)
- [P.4.Cuaderno-html](python-csv-covid19-pandas.html)
- [P.4.Cuaderno-ipnyb](python-csv-covid19-pandas.ipnyb)
- [P.4.Gráfico](practica-4-grafico.png)
- [P.4.Mapa](practica-4-mapa.html)

## Un pasito más 
La falta de tiempo me lo ha impedido pero para seguir avanzando sería interesante en esta práctica [filtrar filas específicas del dataframe](https://pandas.pydata.org/docs/getting_started/intro_tutorials/03_subset_data.html). 
