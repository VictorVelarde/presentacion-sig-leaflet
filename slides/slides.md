#![Leaflet Logo](./resources/logoLeaflet.png)
<hr />   
## Mapas en la Web
<br/>
[@CodersCantabria](https://twitter.com/coderscantabria) - Noviembre, 2017

[@VictorVelarde](https://victorvelarde.github.io) <!-- .element style="margin-top: 60px; color: #57A15E;" -->

===
## ¿Habéis creado alguna vez un mapa para la Web...

===
<div class="redbox">
    <h2>... y os ha salido algo <em>raro<em>?</h2> 
</div>
<!-- .slide: data-background="resources/mapa-invertido.jpg" -->

===
## ¿o con datos "apelotonados"?
![Null Island](./resources/null_island.jpg)
<!-- .slide: data-background="black" -->

===
## Índice
1. Fundamentos de mapas para la Web
2. Un repaso general a Leaflet

===
<div class="box">
    <h2>1º. Fundamentos (espero que útiles...) de mapas para la Web</h2> 
</div>
<!-- .slide: data-background="resources/globos.jpg" -->
Note: 
Intro a algunos conceptos básicos: IG y sistemas de referencia.

==
## Un Mapa presenta 
## **Información Geográfica** <!-- .element style="color: #57A15E;"--> 

==
Y la Información Geográfica (IG) nos permite responder a...
## **¿Dónde está X ...?** <!-- .element class="fragment" data-fragment-index="1" -->  
## **¿Qué hay en Y ...?** <!-- .element class="fragment" data-fragment-index="2" -->  
Note: 
'X' puede ser una mercancía en reparto, un montañero en ruta, un derrame de petróleo, un cliente potencial... | 'Y' como p.ej. restaurantes en un barrio, tipo de vegetación en una parcela, temperatura en un lago, carreteras en un municipio...

== 
# 80% <!-- .element style="color: #57A15E;"-->
## Información ... georreferenciable
(se supone...)
Note:
Es una cita referida a SIG en administraciones locales. Aunque poco contrastada, si revela la importancia intuitiva de "lo geográfico" en muchos proyectos

== 
<div class="box">
    Los 3 componentes de la IG: 
    <em>¿qué?, ¿cuándo?, ¿dónde?</em>
    <h2>Lo especial es lo __espacial__, claro!</h2>
</div>
<!-- .slide: data-background="resources/parcelas.jpg" -->

==
# **SIG:**  <!-- .element style="color: #57A15E;"--> 
## Herramientas para crear, consultar, analizar y **<u>visualizar</u>** IG en Mapas
<img src='resources/gis-electronic.jpg'>
Note:
Pero en esta presentación solo nos centramos en un ámbito muy concreto de los SIG: visualización de mapas en la Web

==
## Pero los **SIG > Mapas web**
(¿quién dijo análisis?) 

==
## Y aquí hablaremos centrados en los **Mapas web**

==
<!-- .slide: data-background="black" -->

== 
## Si queremos crear <u>una web con un mapa</u> con el Centro cívico Callealtero...
<img src='resources/CentroCivico.png' style='height:400px'>

==
## Lo primero es conocer...

==
<div class="box">
    <h2>Las Coordenadas</h2>
    <p>Latitud: 43.4580863 y Longitud: -3.8178212</p>
</div>
<!-- .slide: data-background="resources/brujula-mano.jpg" -->

== 
## La **Cartografía** y la **Geodesia** proporcionan los <u>conceptos</u> principales para entenderlas...

==
<!-- .slide: data-background="black" -->

==
Componente espacial (I)
### La Tierra es un~~a~~ ~~Patata~~ **Geoide**
<img src='resources/geoide.gif'>
Note: Su medición es labor de la Geodesia, pero es una superficie muy compleja e irregular para usarla en posicionamiento.

==
## OK, y ¿cómo se miden coordenadas sobre él...?
###Pfff.... complicado <!-- .element style="color: yellow" class="fragment" data-fragment-index="1" -->  
# ¯\\\_(ツ)\_/¯ <!-- .element style="color: yellow" class="fragment" data-fragment-index="2" -->  

==
Componente espacial (II)
### Mejor algo más sencillo: una **Esfera** o un **Elipsoide**
<img src='resources/elipsoide.jpg'>
Note: Un elipsoide es un modelo que determina el tamaño de la Tierra. Hay varios y se elige uno u otro dependiendo del país o área que se desee representar (a veces "encaja con el geoide más, a veces menos...).

==
El Elipsoide más "famoso" es...
## **WGS84 (usado en los GPS)** <!-- .element style="color: #57A15E;" -->
* S. mayor = 6.378.137,0 m
* S. menor = 6.356.752,314 m
* Geoide - Elipsoide ~= +/- 100m
Note:
SGR80 es equivalente a WGS84 (idéntico semieje mayor, menor difiere en décimas de milímetro). SGR80 se usa en Europa, dentro del ETRS89.

==
## Con el elipsoide ya tenemos la **forma**, pero ¿dónde la colocamos?

==
Componente espacial (III)
## Datum
<img src='resources/datum.png'>
* Se define el punto de contacto de elipsoide y superficie
* Local: NAD 1927, ED 1950... | **Global: WGS84**
* Datum horizontal

== 
Gracias al datum ya podemos medir en superficie con
## **Coordenadas geográficas** <!-- .element style="color: #57A15E;" -->

==
## Vale, y eso nos sirve para un **globo** terráqueo
<img src='resources/globo_persona.jpg'>

==
## ¿Pero si queremos un **mapa 2D** (web / papel)?
<img src='resources/naranja.jpg'><!-- .element class="fragment" data-fragment-index="1" -->  

==
Componente espacial - (y IV)
## La **proyección** es la solución
* Geográficas a Proyectadas (superficie plana)
* Geográficas: ~ grados decimales [-180, -90, 180, 90]
* Proyectadas: ~ metros

==
<div class="box">
    <h3>Toda proyección...</h3>
    <h2>implica una <strong>distorsión</strong></h2>
    <p>(área, ángulo, distancias...)</p>
</div>
<!-- .slide: data-background="resources/mariposa.jpg" -->
Note:
Equidistantes --> conserva las distancias, Equivalentes --> superficies, Conformes --> formas (ángulos).

==
## Web Mercator (I)
## **La Reina en Internet (Google, ESRI...)** <!-- .element style="color: #57A15E;" -->
* **EPSG:3857** (WGS84 + metros)
* Norte arriba | ~ 85ºN a 85ºS
Note: 
Se usa la versión esférica de la proyección, no la elipsoidal, para mayor velocidad en los cálculos. Esto provoca aprox. un 0.33% de distorsión de escala en la dirección Y, algo que no es visualmente perceptible, y simplifica los cálculos.

==
## Web Mercator (II)
<img src='resources/mercator.jpg'>

==
## Web Mercator (III)
<img src='resources/tissot_mercator.png'>

==
## Web Mercator (IV)
### ¿Groenlandia vs Africa? <!-- .element class="fragment" data-fragment-index="1" -->  
<img src='resources/Groenland.png'><!-- .element class="fragment" data-fragment-index="2" -->  

==
<div class="box">
    <h2>¿Ya os habéis dormido?</h2>
</div>
<!-- .slide: data-background="resources/boring.gif" -->

==
### Repasando...
Geoide >> Elipsoide-Esfera >> Datum >> Coordenadas >> Proyecciones (Mercator)
## **[EPSG](http://epsg.io/)** <!-- .element style="color: #57A15E;"-->
<small>(y si no conocemos el EPSG... <u>¡las cosas no cuadran!</u>)</small>

==
## Chuleta
* GPS, KML, GeoJSON, BD: **EPSG: 4326**
* Mapa base Web (GoogleMaps, OSM...): **EPSG:3857**
<!-- .slide: data-background="#57A15E" -->

==
<div class="box">
    <h2>Y ahora algo más divertido</h2>
</div>
<!-- .slide: data-background="resources/shaq.gif" -->


<!-- 2º Leaflet --------------------------------------------------- -->
===
<div class="box">
    <h2>2º. Un repaso general a Leaflet</h2> 
</div>
<!-- .slide: data-background="resources/leaves.jpg" -->

==
## ¿Por qué Leaflet? (I)
* **Gmaps**: El "Pionero" (2005)
* **OpenLayers**: El primero "Libre" (2006)
* **Leaflet**: El "Moderno" (2011, v1.0 en 2016)
Note:
Leaflet como reacción a lo complejo / GIS, rápido y basado en HTML5 y CSS3

==
## ¿Por qué Leaflet? (II)
* Madurez: Clientes y Top 3 en https://unpkg.com/#/stats
<img src='resources/usuarios-leaflet.png'>

==
## ¡SENCILLEZ!
<!-- .slide: data-background="#57A15E" -->

==
## Mapa básico en 4 líneas
```js
var map = L.map('map');
var url = 'http://{s}.tile.osm.org/{z}/{x}/{y}.png';
L.tileLayer(url).addTo(map);
map.setView([0, 0], 0); // [lat, lon], zoom
```
<a href="resources/01-basico.html" data-preview-link>01-basico.html</a>

==
## **Capas** 
* Raster & Vector
* Base & Temáticas (interactivas)

<img src='resources/layers.jpg'>

==
## Raster - Servicios Tiles: **XYZ**
<img src='resources/tilemap.jpeg'>

<a href="https://a.tile.openstreetmap.org/19/256584/191733.png" data-preview-link>Tesela XYZ</a>

==
## Raster - Fuentes WMS
* Estándar OGC
* [WMS IDEE](http://www.idee.es/directorio-de-servicios)
* [Territorio de Cantabria](http://www.territoriodecantabria.es/cartografia-sig/servicios-wms-iig)

==
## Raster - Mapa con WMS
```js
var map = L.map('map');
var url = 'http://www.ign.es/wms-inspire/pnoa-ma';
var options = {layers: 'OI.OrthoimageCoverage'};
var pnoa = L.tileLayer.wms(url, options).addTo(map);
map.setView([43.4703347, -3.8071147], 8);
```
<a href="resources/02-wms.html" data-preview-link>02-wms.html</a>

==
## Vector - Markers y PopUps
```js
var marker = L.marker([lat, lon]);
marker.addTo(map).bindPopup(miHtml);
```
<a href="resources/03-markers.html" data-preview-link>03-markers.html</a>

==
## Vector - GeoJSON
```js
var capa = L.geoJson(data);
map.addLayer(capa);
```
<a href="resources/04-geojson.html" data-preview-link>04-geojson.html</a>

==
## ¿Más funciones?
### **PLUGINS**<!-- .element class="fragment" data-fragment-index="1" -->

==
Plugin (I)
### Mapas de calor con [Leaflet.heat](https://github.com/Leaflet/Leaflet.heat)
<a href="http://leaflet.github.io/Leaflet.heat/demo/" data-preview-link><img src='resources/plugin-heatmap.png'></a>

==
Plugin (II)
### Mapas base de España WMS con [Leaflet.Spain.WMS](https://github.com/sigdeletras/Leaflet.Spain.WMS)
<a href="http://www.sigdeletras.com/Leaflet.Spain.WMS/examples/" data-preview-link><img src='resources/plugin-wms.png'></a>

==
Plugin (III)
### Geocoding con [leaflet-geosearch](https://github.com/smeijer/leaflet-geosearch)
<a href="https://smeijer.github.io/leaflet-geosearch/#openstreetmap" data-preview-link><img src='resources/plugin-geosearch.png'></a>

==
Plugin (IV)
### Animaciones con [Leaflet.TimeDimension](https://github.com/socib/Leaflet.TimeDimension)
<a href="http://apps.socib.es/Leaflet.TimeDimension/examples/" data-preview-link><img src='resources/plugin-timedimension.png'></a>

==
Plugin (V)
### Campos v/e con [Leaflet.CanvasLayer.Field](https://github.com/IHCantabria/Leaflet.CanvasLayer.Field)
<a href="https://ihcantabria.github.io/Leaflet.CanvasLayer.Field/" data-preview-link><img src='resources/plugin-field.png'></a>

==
<div class="redbox">
    <h2>La Comunidad</h2> 
    <ul>
        <li>Decenas de [Plugins](http://leafletjs.com/plugins.html)</li>
        <li>Desarrollos "sobre/compatibles": CARTO, Mapbox, Tangram...</li>
    </ul>
</div>
<!-- .slide: data-background="resources/comunidad.jpg" -->

==
## Oficial Leaflet
* http://leafletjs.com
    * **[API Docs](http://leafletjs.com/reference.html)**
    * [Plugins](http://leafletjs.com/plugins.html)
* [Github](https://github.com/Leaflet/Leaflet)

<!-- 3º Cierre ---------------------------------------------------- -->
===
## Referencias
* ESRI - [Geoide, Elipsoide y Datum](http://desktop.arcgis.com/es/arcmap/latest/map/projections/about-the-geoid-ellipsoid-spheroid-and-datum-and-h.htm)
* OLAYA, V - Libro libre de [Sistemas de Información Geográfica](http://volaya.github.io/libro-sig/)
* AGAFONKIN, V. [Leaflet Story in 13 minutes](https://youtu.be/NLbyHffKQuU)
* Vídeo sobre las distorsiones en área de Web Mercator [Maps that prove you don't really know Earth](https://youtu.be/KUF_Ckv8HbE)
* Wikipedia. [Null Island](https://es.wikipedia.org/wiki/Null_Island)

=== 
![CodersCantabria](./resources/Coders.jpg)  <!-- .element style="border: 0; background: none; box-shadow: none; border-radius: 350px;" -->

<!--
#green: #57A15E
#orange: #ffc156
-->
<!-- .slide: data-background="#000000" -->