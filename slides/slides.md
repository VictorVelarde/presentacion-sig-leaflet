![Leaflet Logo](./resources/logoLeaflet.png)
<hr />   
## y mapas en la Web
<br/>

**[@CodersCantabria](https://twitter.com/coderscantabria) - Noviembre, 2017**

[@VictorVelarde](https://victorvelarde.github.io) <!-- .element style="margin-top: 60px; color: #57A15E;" -->


===
## Índice
1º. Fundamentos de mapas para la Web

2º. Cómo funciona Leaflet


===
## 1º. Fundamentos de mapas para la Web

Note: 
Intro a algunos conceptos básicos: IG y sistemas de referencia.


==
La Información Geográfica (IG) permite responder a...
## **¿Dónde está X ...?** <!-- .element class="fragment" data-fragment-index="1" -->  
## **¿Qué hay en Y ...?** <!-- .element class="fragment" data-fragment-index="2" -->  

Note: 
'X' puede ser una mercancía en reparto, un montañero en ruta, un derrame de petróleo, un cliente potencial... | 'Y' como p.ej. restaurantes en un barrio, tipo de vegetación en una parcela, temperatura en un lago, carreteras en un municipio...


==
# **SIG**  <!-- .element style="color: #57A15E;"--> 
## Sistemas para crear, visualizar, consultar y analizar IG

Note:
Pero en esta presentación solo nos centramos en un ámbito muy concreto de los SIG: visualización de mapas en la Web

== 
# 80% <!-- .element style="color: #ffc156;"-->  
## Información ... georreferenciable 

(se supone...)

Note:
Es una cita referida a SIG en administraciones locales. Aunque poco contrastada, si revela la importancia intuitiva de "lo geográfico".


== 
Los 3 Componentes de la IG

## Temático... ¿qué? <!-- .element class="fragment" data-fragment-index="1" -->  
## Temporal... ¿cuándo? <!-- .element class="fragment" data-fragment-index="2" -->  
## **Espacial... ¿dónde?** <!-- .element style="color: #57A15E;" class="fragment" data-fragment-index="3" -->  


==
## ¿Dónde estoy?
Cómo determinar con precisión la **posición** de un objeto sobre la **superficie terrestre**

Note: Los SIG se basan en los conocimientos de la Geodesia y la Cartografía


== 
## Centro cívico Callealtero
<img src='resources/CentroCivico.png' style='height:400px'>

Latitud: **43.45779** y Longitud: **-3.81964**


==
## ¿Cómo llegar a ésto?
Algunos conceptos de Cartografía y Geodesia


==
Componente espacial (I)
### La Tierra es un **Geoide**
<img src='resources/geoide.png'>

Note: Su medición es labor de la Geodesia, pero es una superficie muy compleja e irregular para usarla en posicionamiento.


==
## OK, y ¿cómo mido sobre ese *pedrolo*...?
# ¯\\\_(ツ)\_/¯ <!-- .element style="color: yellow" class="fragment" data-fragment-index="1" -->  
###Pfff.... complicado <!-- .element style="color: yellow" class="fragment" data-fragment-index="2" -->  


==
Componente espacial (II)
### Mejor más sencillo: un **Elipsoide**
<img src='resources/elipsoide.jpg'>

Note: Un elipsoide es un modelo que determina el tamaño de la Tierra. Hay varios y se elige uno u otro dependiendo del país o área que se desee representar (a veces "encaja con el geoide más, a veces menos...).


==
## Algunos elipsoides "famosos"

|Esferoide|S. mayor (Ecuador)|S. menor|
|--|--|--|
|Clarke 1866|6.378.206,4 m|6.356.583,8 m|
|SGR80|6.378.137.0 m|6.356.752,314 m|
|WGS 1984|6.378.137.0 m|6.356.752,314 m|

SGR80 ~ 
## **WGS84 (GPS)** <!-- .element style="color: #57A15E;" -->

Note:
SGR80 es equivalente a WGS84 (idéntico semieje mayor, menor difiere en décimas de milímetro). SGR80 se usa en Europa, dentro del ETRS89.


==
## Con el elipsoide ya tenemos la **forma**, pero ¿dónde la colocamos?


==
Componente espacial (III)
## Datum
<img src='resources/datum.png'>

- Define el punto de contacto de elipsoide y superficie
- **Local**: NAD 1927, ED 1950... | **Global**: WGS84
- Datum horizontal


== 
## Gracias al datum ahora ya podemos medir en superficie
### **Coordenadas geográficas** <!-- .element style="color: #57A15E;" -->


==
## Vale, pero eso solo me sirve para un globo terráqueo
<img src='resources/globo_persona.jpg'>


==
## ¿Y si quiero un mapa en pantalla (o papel)?
<img src='resources/naranja.jpg'>


==
Componente espacial - (y IV)
## La **proyección** es la solución
### matemática para la conversión de coordenadas Tierra > Papel


==
## Toda proyección

==
## ¿Para qué tanto lío?
Si no conocemos el sistema de referencia de un dato, ¡las cosas no cuadran!


==
## Chuleta básica para Mapas web <!-- .element style="color: red;" -->
GPS, KML, GeoJSON --> por defecto, longitud & latitud WGS84 (**EPSG: 4326**)
Mapa base (GoogleMaps, OSM...) --> Web Mercator (**EPSG:3857**)


==
## Mercator

Note: 
To simplify the calculations, we use the spherical form of this projection, not the ellipsoidal form. Since the projection is used only for map display, and not for displaying numeric coordinates, we don’t need the extra precision of an ellipsoidal projection. The spherical projection causes approximately 0.33% scale distortion in the Y direction, which is not visually noticeable.


<!-- 2º Leaflet --------------------------------------------------- -->
===
## 2º. Leaflet
<!-- .slide: data-background="resources/logoLeaflet.png" -->

== 
## Breve historia
<!-- .slide: data-background="#57A15E" -->
Note: Aparición ante GMaps, madurez, casos de éxito.

== 
## Conceptos básicos SIG

Capas raster/vector, 
Software SIG: BD, Escritorio, Web
Formatos de datos y cómo encaja Leaflet en ese contexto.


<!-- 3º Futuro ---------------------------------------------------- -->
===
## 3º. Futuro


<!-- 4º Cierre ---------------------------------------------------- -->
===
## Referencias
* ESRI - [Geoide, Elipsoide y Datum](http://desktop.arcgis.com/es/arcmap/latest/map/projections/about-the-geoid-ellipsoid-spheroid-and-datum-and-h.htm)
* OLAYA, V - Libro libre de [Sistemas de Información Geográfica](http://volaya.github.io/libro-sig/)

=== 
![CodersCantabria](./resources/Coders.jpg)  <!-- .element style="border: 0; background: none; box-shadow: none; border-radius: 350px;" -->

<!--
#green: #57A15E
#orange: #ffc156
-->