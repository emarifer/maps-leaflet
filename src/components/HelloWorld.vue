<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this library,<br>
      check out the Leaflet documentation.
      <a href="https://leafletjs.com/" target="_blank" rel="noopener">Leaflet documentation</a>.
    </p>
    <h3>Installed Plugins:</h3>
    <ul>
      <li><a href="https://leafletjs.com/" target="_blank" rel="noopener">Leaflet</a></li>
      <li><a href="https://vue2-leaflet.netlify.app/" target="_blank" rel="noopener">Vue Leaflet</a></li>
      <li><a href="https://github.com/mpetazzoni/leaflet-gpx" target="_blank" rel="noopener">leaflet-gpx</a></li>
    </ul>
    <h3>Essential Links</h3>
    <div class="custom">
      <ul>
        <li><a href="https://codingpotions.com/vue-props" target="_blank" rel="noopener">Cómo crear y usar los props en VueJS</a></li>
        <li><a href="https://www.danielprimo.io/blog/leaflet-una-alternativa-gratis-a-google-maps" target="_blank" rel="noopener">Leaflet, una alternativa a Google Maps</a></li>
        <li><a href="https://stackoverflow.com/questions/54060555/how-to-show-multiple-maps-on-one-html-page" target="_blank" rel="noopener">How to show multiple maps on one html page</a></li>
        <li><a href="https://mappinggis.com/2018/09/publicacion-web-de-datos-gps-con-leaflet/" target="_blank" rel="noopener">Visualización de datos GPS en mapas web con Leaflet</a></li>
        <li><a href="https://leaflet-extras.github.io/leaflet-providers/preview/" target="_blank" rel="noopener">Leaflet-providers preview</a></li>
        <li><a href="https://github.com/sigdeletras/Leaflet.Spain.WMS" target="_blank" rel="noopener">Leaflet.Spain.WMS</a></li>
        <li><a href="https://stackoverflow.com/questions/61389223/leaflet-change-marker-for-wpt" target="_blank" rel="noopener">Leaflet change marker for wpt</a></li>
        <li><a href="https://jsfiddle.net/31ws6z37/" target="_blank" rel="noopener">leaflet map: update marker using navigator.geolocation.watchPosition?</a></li>
      </ul>
    </div>
    <div class="footer">
      <hr>
      <h4>If you are a developer look / download<br>the code from <a href="https://github.com/emarifer/maps-leaflet" target="_blank" rel="noopener">here</a></h4>
    </div>
  </div>
</template>

<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
  .footer {
    width: 100%;
    text-align: center;
    position: fixed;
    bottom: 0;
    background-color: #fff;
    z-index: 100;
  }
  hr, h4 {
    padding: 0.1rem;
    width: 90%;
  }
  .custom ul {
    margin-bottom: 6rem;
  }
  .custom li {
    display: block;
  }
</style>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>
