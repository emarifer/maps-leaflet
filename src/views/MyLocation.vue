<template>
    <div>
        <h1>My Location</h1>
        <!-- style="width:100%;height:500px; z-index:1;" -->
        <div id="map_2385853" class="map"></div>
    </div>
</template>

<style scoped>
    .map {
        height: 500px;
        margin-left: 1.5rem;
        margin-right: 1.5rem;
        box-shadow: 10px 10px 10px rgba(0, 0, 0, .3);
    }
</style>

<script>
    import L from 'leaflet';
    import { Icon } from 'leaflet';

    export default {
        name: 'MyLocation',
        mounted() {
            delete Icon.Default.prototype._getIconUrl;
            Icon.Default.mergeOptions({
                iconRetinaUrl: require('leaflet/dist/images/marker-icon-2x.png'),
                iconUrl: require('leaflet/dist/images/marker-icon.png'),
                shadowUrl: require('leaflet/dist/images/marker-shadow.png'),
            });

            let watchID;
            let geoLoc;

            function showLocation(position) {
                let latitude = position.coords.latitude;
                let longitude = position.coords.longitude;
            }

            function errorHandler(err) {
                if (err.code == 1) {
                    alert("Error: Access is denied!");
                }

                else if (err.code == 2) {
                    alert("Error: Position is unavailable!");
                }
            }

            function getLocationUpdate() {
                if (navigator.geolocation) {
                    // timeout at 60000 milliseconds (60 seconds)
                    const options = { timeout: 60000 };
                    geoLoc = navigator.geolocation;
                    watchID = geoLoc.getCurrentPosition(showLocation, errorHandler, options);
                    // watchID = geoLoc.watchPosition
                    const map = L.map('map_2385853');

                    const googleMaps = L.tileLayer('http://{s}.google.com/vt/lyrs=m&x={x}&y={y}&z={z}', {
                        maxZoom: 22,
                        subdomains: ['mt0', 'mt1', 'mt2', 'mt3']
                    }).addTo(map);

                    L.control.scale({ options: { position: 'bottomleft', metric: true } }).addTo(map);

                    /*L.tileLayer('http://{s}.google.com/vt/lyrs=m&x={x}&y={y}&z={z}', {
                    attribution: 'Map data &copy; <a href="http://openstreetmap.org">OpenStreetMap</a> contributors, <a href="http://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="http://cloudmade.com">CloudMade</a>',
                    maxZoom: 18
                    }).addTo(map);*/

                    map.locate({ setView: true, maxZoom: 16 });
                    function onLocationFound(e) {
                        const radius = e.accuracy / 2;
                        L.marker(e.latlng).addTo(map)
                            .bindPopup(`You are less than ${radius} meters from this point`)
                            .openPopup();
                        L.circle(e.latlng, radius).addTo(map);
                    }
                    map.on('locationfound', onLocationFound);
                }

                else {
                    alert("Sorry, browser does not support geolocation!");
                }
            }

            getLocationUpdate();
        }
    }
</script>