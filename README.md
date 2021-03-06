# BiciMAD
Proyecto para visualización de datos de bicimad.

Integrantes:
* Alejandro Galvis
* Daniel Guerrero
* Gastón Legnani
* Jaime Galindo
* Roberto Barrios

Aprovechamos el trabajo, para insertar los datos limpios y trandformados en la base de datos que nos obligan armar para el TFM. Por eso puede que en algun archivo exista código con tal fin. En la mayoría de los casos, está comentado para que no vuelva a ejecutarse. Por ese motivo si se ejecuta puede que de error, ya que la conexión a la base de datos es incorrecta.

Hay 3 carpetas dentro del repositorio.
- **dat** que contiene los archivos con los datos utilizados para el análisis tanto en R como en Python.
- **R** que contiene los scripts y markdowns de R.
- **Python** que contiene los notebook del análisis realizado en Python.

## Python

Se analizan varias fuentes de datos por separado. Se encuentran los siguientes archivos:

* **Calidad del aire - Madrid** . Analiza los datos de la contaminación de Madrid en el período 2015-2018. Los datos fueron obtenidos desde el catálogo de datos abiertos.

* **Clima Madrid** .  Se obtienen los datos desde el 2015 a principios de febrero 2019, a través de la Api de la AEMET. Esos datos están descargados en un archivo en la carpeta dat. De todas formas se puede consultar la API para cualquier periodo y utilizar esos datos en el análisis (Está explicado en el notebook). Esta información se cruza luego con los usos de las bicicletas.

* **Estaciones Bicimad en tiempo real** . Se obtiene la información del estado de las situaciones de Bicimad en tiempo real (mediante API) y se visualiza en mapa cada una diferenciandose según la disponibilidad que tengan en ese momento. Además se aprovecha esa información para guardar en BD las estaciones y su información general.

**Nota** En una computadora al ejecutar la visualización en mapa de este notebook. No supimos identificar por qué pero creemos tiene algo que ver con la versión de folium. El error era el siguiente: "no arguments in initialization list". Por lo que investigamos tenia que ver con el crs definido arriba.
No supimos solucionarlo, además en otras 3 computadoras todo funcionaba correctamente asi que esperamos funcione bien donde se realize la corrección.

* **Usos Bicimad por día** . Se analiza según los datos obtenidos del catalogo abierto de madrid, los usos de las biciletas según distintos criterios, en el periodo 2015- 2018. Se guarda además la información en la base de datos. Este análisis está repetido en otro notebook. Se hizo dos veces por un error de comunicación, pero llega a distintas conclusiones con los gráficos.

* **Accidentes Bicicletas**
Se obtienen los datos de los accidentes con implicaciones de bicicletas. El archivo fue obtenido desde el catálogo de datos abiertos. Se hace una limpieza de la información y un analisis visual de los datos. Tomamos los archivos del 2016, 2017 y 2018 y los unimos en un archivo maestro. 

* **Usos Bicimad vs clima**
Se obtienen los datos del uso del sistema Bicimad, los cuales cuentan con fecha por día, tipo de usuario (Abonado anual/Abonado ocasional) y cantidades de uso por tipo de usuario. Adicionalmente se realiza un cruce con la base de datos del clima para identificar posibles relaciones entre la lluvia y la temperatura con el uso de las bicicletas.

## R

**Nota importante**. Hemos tenido unos problemas con los acentos y con las ñ al subir y bajar los archivos en distinas computadoras. Hay un caso puntual en el de accidentes donde se hace un gsub por "Años" que en algunos casos se vuelve "A?os" y una de las gráficas no se genera correctamente. No supimos como solucionarlo ya que con la opción Reopen with encoding no se arregla. En todo caso verificar funcionamiento con el Html generado para ese markdown.

* **Calidad_del_aire**. Analiza los datos de la contaminación de Madrid en el periodo 2015-2018. Los datos fueron obtenidos desde el catálogo de datos abiertos.

Hay dos archivos. _"Calidad del aire.rmd"_ donde se puede visualizar el código y un archivo llamado _"Calidad del aire.html"_ donde ya se visualiza el markdown ejecutado en formato Html. Para visualizar el resultado, se recomienda ir directo al archivo html ya que el markdown tarda un poco en completar de ejecutarse, debido a varios cálculos que realiza.

* **Estacionesbicimad en tiempo real**. Dentro de la carpeta R, existe una carpeta llamada "estacionesbicimad" que contiene un markdown integrado con una aplicación shiny ("_estaciones_tiempo_real.Rmd_"). Se muestra de forma interactiva la disponibilidad de bicicletas y la información de las estaciones en tiempo real, utilizando una API con tal fin. (Servicios abiertos Open Data Madrid)

* **Mapa de ocupacion de estaciones**.  Dentro de la carpeta R, se generó un markdown integrado con una aplicación de shiny (archivo llamado _Mapa_de_ocupacion_de_estaciones.Rmd_ para mostrar de forma interactiva la disponibilidad de bicicletas según el dia y la hora que desee el usuario (**Datos de noviembre 2018**), utilizando para ello un json. (en este markdown, no se pusieron tildes en las palabras ya que fallaba al ejecutarla en otro ordenador, esto era a pesar de ser un comentario)
**Tarda unos minutos** ya que lee y procesa un archivo de 1GB que está almacenado en un servidor de Estados Unidos

* **Estaciones_estado_201811(Mapa de calor)**. Dentro de la carpeta R, se generó un markdown integrado con una aplicación de shiny para mostrar (_Llamado Estaciones_estado_201811(Mapa de calor).Rmd_) de forma interactiva la disponibilidad de bicicletas a través de un mapa de calor. Usa la misma base de datos que el markdown anterior. Noviembre de 2018. (en este markdown, no se pusieron tildes en las palabras ya que fallaba al ejecutarla en otro ordenador, esto era a pesar de ser un comentario)
**Tarda unos minutos** ya que lee y procesa un archivo de 1GB que está almacenado en un servidor de Estados Unidos

* **Informe_uso_bicimad_markdown** Dentro de la carpeta R se generó un informe sobre el comportamiento de la demanda del sistema de Bicimad en relación a dos tipos de usuarios, los abonados anuales y los abonados ocasionales. Se representa las distribuciones de la demanda por año, por meses y días de la semana. Adicionalmente se cruza con la base de datos del clima para identificar relaciones entre el uso del sistema y la lluvia y la temperatura. El archivo esta en formato Markdown y html.

* **Accidentes**
Se obtienen los datos de los accidentes con implicaciones de bicicletas. El archivo fue obtenido desde el catálogo de datos abiertos. Se hace una limpieza de la información y un análisis visual de los datos. Hay dos archivos. _"Accidentes.rmd"_ donde se puede visualizar el código y un archivo llamado _"Accidentes.html"_ donde ya se visualiza el markdown ejecutado en formato Html.
