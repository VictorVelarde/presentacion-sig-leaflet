#![Leaflet Logo](./resources/logoLeaflet.png)
<hr />   
## Mapas en la Web
<br/>

**[@CodersCantabria](https://twitter.com/coderscantabria) - Noviembre, 2017**

[@VictorVelarde](https://victorvelarde.github.io) <!-- .element style="margin-top: 60px; color: #57A15E;" -->


===
## Índice
1. Fundamentos de mapas para la Web
2. Un repaso general a Leaflet


===
<div class="box">
    <h2>1º. Fundamentos de mapas para la Web</h2> 
</div>
<!-- .slide: data-background="resources/globos.jpg" -->

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
## Sistemas para crear, consultar, analizar y **visualizar** IG en Mapas

<img src='resources/gis-electronic.jpg'>

Note:
Pero en esta presentación solo nos centramos en un ámbito muy concreto de los SIG: visualización de mapas en la Web

== 
# 80% <!-- .element style="color: #ffc156;"-->  
## Información ... georreferenciable 

(se supone...)

Note:
Es una cita referida a SIG en administraciones locales. Aunque poco contrastada, si revela la importancia intuitiva de "lo geográfico".


== 
<div class="box">
    Los 3 componentes de la IG
    <h2>Temático... ¿qué?</h2>
    <h2>Temporal... ¿cuándo?</h2>
    <h2><strong>Espacial</strong>... ¿dónde?</h2>
</div>
<!-- .slide: data-background="resources/parcelas.jpg" -->


==
<div class="box">
    <h2>¿Dónde?</h2> 
    <p>Cómo determinar con precisión la <strong>posición</strong> de un objeto sobre la superficie terrestre</p>
</div>
<!-- .slide: data-background="resources/mapa-pin.jpg" -->

Note: Los SIG se basan en los conocimientos de la Geodesia y la Cartografía


== 
## Centro cívico Callealtero
<img src='resources/CentroCivico.png' style='height:400px'>

Latitud: **43.45779** y Longitud: **-3.81964**


==
<div class="box">
    <h2> ¡Coordenadas!</h2>
    Algunos conceptos de Cartografía y Geodesia
</div>
<!-- .slide: data-background="resources/brujula-mano.jpg" -->


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
### Mejor en algo más sencillo: un **Elipsoide** o una **Esfera**
<img src='resources/elipsoide.jpg'>

Note: Un elipsoide es un modelo que determina el tamaño de la Tierra. Hay varios y se elige uno u otro dependiendo del país o área que se desee representar (a veces "encaja con el geoide más, a veces menos...).


==
### El Elipsoide más "famoso" es

## **WGS84 (GPS)** <!-- .element style="color: #57A15E;" -->
~ SGR80 (ETRS89 - Europa)

|S. mayor (Ecuador)|S. menor|
|--|--|
|6.378.137.0 m|6.356.752,314 m|


Note:
SGR80 es equivalente a WGS84 (idéntico semieje mayor, menor difiere en décimas de milímetro). SGR80 se usa en Europa, dentro del ETRS89.


==
## Con el elipsoide ya tenemos la **forma**, pero ¿dónde la colocamos?


==
Componente espacial (III)
## Datum
<img src='resources/datum.png'>

* Define el punto de contacto de elipsoide y superficie
* **Local**: NAD 1927, ED 1950... | **Global**: WGS84
* Datum horizontal


== 
## Gracias al datum ahora ya podemos medir en superficie
### **Coordenadas geográficas** <!-- .element style="color: #57A15E;" -->


==
## Vale, pero eso solo me sirve para un **globo** terráqueo
<img src='resources/globo_persona.jpg'>


==
## ¿Y si quiero un mapa en pantalla (o papel)?
<img src='resources/naranja.jpg'>
## 3D !== 2D


==
Componente espacial - (y IV)
## La **proyección** es la solución

* Geográficas a Proyectadas (superficie plana)
* Geográficas: ~ grados decimales [-180, -90, 180, 90]
* Proyectadas: ~ metros


==
## Toda proyección...
### implica una **distorsión**
### (área, ángulo, distancias...)

Note:
Equidistantes --> conserva las distancias, Equivalentes --> superficies, Conformes --> formas (ángulos).


==
## Web Mercator (I)
### **La Reina en Internet** (GoogleMaps, Bing, ESRI, OSM...)
* EPSG:3857 (WGS84 + metros)
* No hay polos! (~ 85ºN a 85ºS)
* Norte arriba

Note: 
Se usa la versión esférica de la proyección, no la elipsoidal, para mayor velocidad en los cálculos. Esto provoca aprox. un 0.33% de distorsión de escala en la dirección Y, algo que no es visualmente perceptible, y simplifica los cálculos.


==
## Mercator (II)
<img src='resources/mercator.jpg'>


==
## Mercator (III)
<img src='resources/tissot_mercator.png'>


==
## PUNTOS CLAVE 
### Mapas en la web
* Si no conocemos el sistema de referencia (EPSG)... **¡las cosas no cuadran!**
* GPS, KML, GeoJSON...: **EPSG: 4326**
* Mapa base (GoogleMaps, OSM...: **EPSG:3857**


<!-- 2º Leaflet --------------------------------------------------- -->
===
<div class="box">
    <h2>2º. Un repaso general a Leaflet</h2> 
</div>
<!-- .slide: data-background="resources/leaves.jpg" -->>

== 
## Breve historia
<!-- .slide: data-background="#57A15E" -->
Note: Aparición ante GMaps, madurez, casos de éxito.

== 
## Conceptos generales SIG
* Capa de información: ráster / vector
* Software: escritorio / BD / Web
* Formatos de datos y cómo encaja Leaflet en ese contexto.


<!-- 3º Cierre ---------------------------------------------------- -->
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
<!-- .slide: data-background="#000000" -->