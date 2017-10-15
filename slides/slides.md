![Leaflet Logo](./resources/logoLeaflet.png)
<hr />   
# SIG & Mapas Web
<br/>

**[@CodersCantabria](https://twitter.com/coderscantabria) - Noviembre, 2017**
**@VictorVelarde** <!-- .element style="margin-top: 60px; color: #57A15E;" -->


===
## Índice
* SIG
* Mapas en la Web y Leaflet
* Futuro


===
## 1º. SIG, IG y Mapas
<!-- //.slide: data-background="#ff0000" -->

Note: 
Intro a los SIG, para entender algunos conceptos básicos: IG y sistemas de referencia. Capas, raster/vector, componentes (BD, Escritorio, Web), mapas en la web y cómo encaja Leaflet en ese contexto.


==
La Información Geográfica permite responder a...
## ¿**Dónde** está X ...? 
## ¿Qué hay **en** Y ...?

Note: 
'X' puede ser una mercancía en reparto, un montañero en ruta, un derrame de petróleo, un cliente potencial... | 'Y' como p.ej. restaurantes en un barrio, tipo de vegetación en una parcela, temperatura en un lago, carreteras en un municipio...


== 
# 80% <!-- .element style="color: #57A15E;"-->  
## Información ... georreferenciable 

Note:
Es una cita referida a SIG en administraciones locales. Aunque poco contrastada, si revela la importancia intuitiva de "lo geográfico".


== 
Los 3 Componentes de la IG

## Temático <!-- .element class="fragment" data-fragment-index="1" -->  
## Temporal <!-- .element class="fragment" data-fragment-index="2" -->  
## **Espacial** <!-- .element style="color: #57A15E;" class="fragment" data-fragment-index="3" -->  


==
## ¿Dónde estoy?
¿Cómo determinar con precisión la posición de un objeto sobre la **Superficie Terrestre**?

Note: Los SIG se basan en los conocimientos de la Geodesia y la Cartografía


==
Componente espacial - I
### La Tierra es un Geoide...
<img src='resources/geoide.png'>

Note: Su medición es labor de la Geodesia, pero es una superficie muy compleja e irregular para usarla en posicionamiento.


==
## OK, y ¿cómo mido sobre ese 
# pedrolo...?
###Pfff.... complicado<!-- .element style="color: red" class="fragment" data-fragment-index="1" -->  


==
Componente espacial - II
### Mejor con algo más sencillo, como un Elipsoide...
<img src='resources/elipsoide.jpg'>

Note: Un elipsoide determina el tamaño de la Tierra. Hay varios y se elige uno u otro dependiendo del país o área que se desee representar (a veces "encaja con el geoide más, a veces menos...).


==
## Algunos elipsoides "famosos"

|Esferoide|S. mayor (Ecuador)|S. menor|
|--|--|--|
|Clarke 1866|6.378.206,4 m|6.356.583,8 m|
|SGR80|6.378.137.0 m|6.356.752,314 m|
|**WGS 1984**|6.378.137.0 m|6.356.752,314 m|

SGR80 ~ WGS84

Note:
SGR80 es equivalente a WGS84 (idéntico semieje mayor, menor difiere en décimas de milímetro). SGR80 se usa en Europa, dentro del ETRS89.

==
##Datum

Local: NAD 1927 | ED 1950
Global: WGS 84


==
Componente espacial - III
### Una proyección es...

Un mecanismo para representar en pantalla o papel coordenadas referidas a la superficie curva de la Tierra

== 
Sistema de referencia: 

==
## Mapas web


==
## Mercator

Note: 
To simplify the calculations, we use the spherical form of this projection, not the ellipsoidal form. Since the projection is used only for map display, and not for displaying numeric coordinates, we don’t need the extra precision of an ellipsoidal projection. The spherical projection causes approximately 0.33% scale distortion in the Y direction, which is not visually noticeable.

==
## SIG


<!-- 2º Leaflet --------------------------------------------------- -->
===
## 2º. Leaflet
<!-- .slide: data-background="resources/logoLeaflet.png" -->

== 
## Breve historia
<!-- .slide: data-background="#57A15E" -->
Note: Aparición ante GMaps, madurez, casos de éxito.

<!-- 3º Futuro ---------------------------------------------------- -->
===
## 3º. Futuro
<!-- .slide: data-background="#ffc156" -->


<!-- 4º Cierre ---------------------------------------------------- -->
===
## Contacto

|||
|-|-|
|github.io|[https://victorvelarde.github.io](https://victorvelarde.github.io/)|
|email|[victor.velarde@gmail.com](mailto:victor.velarde@gmail.com)|
|||

===
## Referencias
* ESRI - [Geoide, Elipsoide y Datum](http://desktop.arcgis.com/es/arcmap/latest/map/projections/about-the-geoid-ellipsoid-spheroid-and-datum-and-h.htm)
* OLAYA, V - Libro libre de [Sistemas de Información Geográfica](http://volaya.github.io/libro-sig/)

=== 
![CodersCantabria](./resources/Coders.jpg)  <!-- .element style="border: 0; background: none; box-shadow: none; border-radius: 350px;" -->

