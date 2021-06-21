<template>
  <div class="container">
    <h1>Maps of Some Cities of the World</h1>
    <Map v-for="(data, index) in dataMap" :key="index" :data="data" />
  </div>
</template>

<script>
  // @ is an alias to /src
  import Map from '@/components/Map.vue'

  export default {
    name: 'CitiesMaps',
    components: {
      Map,
    },
    data() {
      return {
        dataMap: [
          {
            // url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
            zoom: 13,
            center: [51.505, -0.09],
            markerLatLng: [51.505, -0.09],
            city: 'London',
          },
          {
            // url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
            zoom: 13,
            center: [52.520007,13.404954],
            markerLatLng: [52.520007,13.404954],
            city: 'Berlin',
          },
          {
            // url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
            zoom: 13,
            center: [55.755826,37.6173],
            markerLatLng: [55.755826,37.6173],
            city: 'Moscow',
          },
          {
            // url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
            zoom: 13,
            center: [37.774929,-122.419416],
            markerLatLng: [37.774929,-122.419416],
            city: 'San Francisco',
          },
          {
            // url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
            zoom: 13,
            center: [45.9230083, 6.8701887],
            markerLatLng: [45.9230083, 6.8701887],
            city: 'Chamonix-Mont-Blanc',
          },
        ],
      }
    },    
  }
</script>