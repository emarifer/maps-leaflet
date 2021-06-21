<template>
    <div class="maps">
        <h4>{{ data.city }}</h4>
        <div class="shadow">
            <l-map :zoom="data.zoom" :center="data.center" ref="map">
                
                <l-control-scale position="topright" :imperial="false" :metric="true"></l-control-scale>
                
                <l-control-layers position="topright"  ></l-control-layers>

                <l-tile-layer
                    v-for="tileProvider in tileProviders"
                    :key="tileProvider.name"
                    :name="tileProvider.name"
                    :visible="tileProvider.visible"
                    :url="tileProvider.url"
                    :attribution="tileProvider.attribution"
                    layer-type="base"/>

                <l-marker :lat-lng="data.markerLatLng">
                    <l-popup>Hello! I'm here:<br><strong>{{ data.city }}</strong></l-popup>
                </l-marker>
                <!-- <l-gpx :gpx-file="require('../tracks/test.gpx')" @gpx-loaded="onGpxLoaded" /> -->
            </l-map>
        </div>
    </div>
</template>

<style scoped>
    .maps {
        padding-left: 1.5rem;
        padding-right: 1.5rem;
        padding-bottom: 4rem;
    }

    .shadow {
        height: 350px;
        box-shadow: 10px 10px 10px rgba(0, 0, 0, .3);
    }
</style>

<script>
    import L from 'leaflet';
    import { Icon } from 'leaflet';
    import { LMap, LTileLayer, LWMSTileLayer, LMarker, LPopup, LControlScale, LControlLayers } from 'vue2-leaflet';
    // import '../../node_modules/vue2-leaflet-gpx/dist/vue2-leaflet-gpx.umd.js';

    export default {
        name: 'CitiesMaps',
        components: {
            LMap,
            LTileLayer,
            LMarker,
            LPopup,
            LControlScale,
            LControlLayers,
        },
        data() {
            return {
                tileProviders: [
                    {
                    name: 'OpenStreetMap',
                    visible: true,
                    attribution:
                        '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
                    url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
                    },
                    {
                    name: 'OpenTopoMap',
                    visible: false,
                    url: 'https://{s}.tile.opentopomap.org/{z}/{x}/{y}.png',
                    attribution:
                        'Map data: &copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>, <a href="http://viewfinderpanoramas.org">SRTM</a> | Map style: &copy; <a href="https://opentopomap.org">OpenTopoMap</a> (<a href="https://creativecommons.org/licenses/by-sa/3.0/">CC-BY-SA</a>)',
                    },
                    {
                    name: 'Esri.WorldImagery',
                    visible: false,
                    url: 'https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}',
                    attribution:
                        'Tiles &copy; Esri &mdash; Source: Esri, i-cubed, USDA, USGS, AEX, GeoEye, Getmapping, Aerogrid, IGN, IGP, UPR-EGP, and the GIS User Community',
                    },
                ],
            }
        },
        mounted() {
            delete Icon.Default.prototype._getIconUrl;
            Icon.Default.mergeOptions({
                iconRetinaUrl: require('leaflet/dist/images/marker-icon-2x.png'),
                iconUrl: require('leaflet/dist/images/marker-icon.png'),
                shadowUrl: require('leaflet/dist/images/marker-shadow.png'),
            });
        },
        props: {
            data: {
                url: String,
                zoom: Number,
                center: Array,
                markerLatLng: Array,
                city: String
            }
        },
        // methods: {
        //     onGpxLoaded(e) {
        //         const { mapObject } = this.$refs.map;
        //         const gpxMapObject = e.target;
        //         mapObject.fitBounds(gpxMapObject.getBounds());
        //     }
        // },
    }
</script>