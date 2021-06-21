<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/maps">Cities Maps</router-link> |
      <router-link to="/mymaps">Topographic Maps of Spain</router-link> |
      <router-link to="/mylocation">My Location</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  #nav {
    padding: 30px;
  }

  #nav a {
    font-weight: bold;
    color: #2c3e50;
  }

  #nav a.router-link-exact-active {
    color: #42b983;
  }
</style>


<!-- 
  DOCUMENTATION:

  LEAFLET-PROVIDERS PREVIEW. VER;
  https://leaflet-extras.github.io/leaflet-providers/preview/
  
  <li><a href="https://leafletjs.com/" target="_blank" rel="noopener">Leaflet</a></li>

  <li><a href="https://vue2-leaflet.netlify.app/" target="_blank" rel="noopener">Vue Leaflet</a></li>

  <li><a href="https://github.com/mpetazzoni/leaflet-gpx" target="_blank" rel="noopener">leaflet-gpx</a></li>

  <li><a href="https://codingpotions.com/vue-props" target="_blank" rel="noopener">Cómo crear y usar los props en VueJS</a></li>

  <li><a href="https://www.danielprimo.io/blog/leaflet-una-alternativa-gratis-a-google-maps" target="_blank" rel="noopener">Leaflet, una alternativa a Google Maps</a></li>

  <li><a href="https://stackoverflow.com/questions/54060555/how-to-show-multiple-maps-on-one-html-page" target="_blank" rel="noopener">How to show multiple maps on one html page</a></li>

  <li><a href="https://mappinggis.com/2018/09/publicacion-web-de-datos-gps-con-leaflet/" target="_blank" rel="noopener">Visualización de datos GPS en mapas web con Leaflet</a></li>

  <li><a href="https://github.com/sigdeletras/Leaflet.Spain.WMS" target="_blank" rel="noopener">Leaflet.Spain.WMS</a></li>

  <li><a href="https://stackoverflow.com/questions/61389223/leaflet-change-marker-for-wpt" target="_blank" rel="noopener">Leaflet change marker for wpt</a></li>

  LEAFLET MAP: UPDATE MARKER USING MAP.LOCATE.
  LEAFLET MAP: HOW TO REMOVELAYER AND ADD POPUPS TO THE MAP?. VER:
  https://stackoverflow.com/questions/40438868/leaflet-map-how-to-removelayer-and-add-popups-to-the-map
  https://jsfiddle.net/31ws6z37/5/

  MENOS RELEVANTE:
  LEAFLET MAP: UPDATE MARKER USING MAP.LOCATE. VER;
  https://stackoverflow.com/questions/40433317/leaflet-map-update-marker-using-navigator-geolocation-watchposition

  <li><a href="https://jsfiddle.net/31ws6z37/" target="_blank" rel="noopener">leaflet map: update marker using navigator.geolocation.watchPosition?</a></li>
 -->