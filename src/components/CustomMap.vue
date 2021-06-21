<template>
    <div class="container">
        <h4>{{ location }}</h4>
        <div :id="mapId" class="map"></div>
    </div>
</template>

<style scoped>
    .container {
        height: 350px;
        padding-left: 1.5rem;
        padding-right: 1.5rem;
        padding-bottom: 4rem;
    }

    .map {
        /* width: 100%; */
        /* margin: auto; */
        height: 100%;
        box-shadow: 10px 10px 10px rgba(0, 0, 0, .3);
    }
</style>

<script>
    import L from 'leaflet';
    import { Icon } from 'leaflet';
    import '../../node_modules/leaflet-gpx/gpx.js';

    export default {
        name: 'CustomMap',
        mounted() {
            delete Icon.Default.prototype._getIconUrl;
            Icon.Default.mergeOptions({
                iconRetinaUrl: require('leaflet/dist/images/marker-icon-2x.png'),
                iconUrl: require('leaflet/dist/images/marker-icon.png'),
                shadowUrl: require('leaflet/dist/images/marker-shadow.png'),
            });

            const Spain_MapasrasterIGN = L.tileLayer.wms('http://www.ign.es/wms-inspire/mapa-raster', {
                layers: 'mtn_rasterizado',
                format: 'image/png',
                transparent: false,
                continuousWorld: true,
                attribution: '© <a href="http://www.ign.es/ign/main/index.do" target="_blank">Instituto Geográfico Nacional de España</a> contributors'
            });

            const Spain_PNOA_Ortoimagen = L.tileLayer.wms('http://www.ign.es/wms-inspire/pnoa-ma', {
                layers: 'OI.OrthoimageCoverage',
                format: 'image/png',
                transparent: false,
                continuousWorld: true,
                attribution: 'PNOA cedido por © <a href="http://www.ign.es/ign/main/index.do" target="_blank">Instituto Geográfico Nacional de España</a> contributors'
            });

            const map = L.map(this.mapId, {
                layers: [
                    Spain_MapasrasterIGN,
                ]
            })/* .setView([38.3162626, -2.5852934], 18) */;

            const baseMaps = {
                "Spain_MapasrasterIGN": Spain_MapasrasterIGN,
                "Spain_PNOA_Ortoimagen": Spain_PNOA_Ortoimagen
            };

            L.control.layers(baseMaps).addTo(map);

            // L.marker([38.3162626, -2.5852934])
            //     .bindPopup("I'm here:<br><strong>Navalperal (1640 m)</strong>")
            //     .openPopup()
            //     .addTo(map);

            // const url = 'tracks/las-acebeas-navalperal-sierra-de-segura-.gpx';
            new L.GPX(this.url, {
                async: true,
                marker_options: {
                    wptIconUrls: {
                        '': 'images/pin-icon-wpt.png',
                    },
                    startIconUrl: 'images/pin-icon-start.png',
                    endIconUrl: 'images/pin-icon-end.png',
                    shadowUrl: 'images/pin-shadow.png'
                }
            }).on('loaded', (e) => {
                map.fitBounds(e.target.getBounds());
            }).addTo(map);


            L.control.scale({ options: { position: 'bottomleft', metric: true } }).addTo(map);
        },
        props: {
            location: String,
            mapId: String,
            url: String,
            // coords: Array
        },
    }
</script>

<!-- ICONOS DE WPT EN LEAFLET-GPX. VER:
    https://stackoverflow.com/questions/61389223/leaflet-change-marker-for-wpt
-->