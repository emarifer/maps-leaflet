<template>
    <div>
        <h1>Topographic Maps of Spain</h1>
        <CustomMap v-for="(data, index) in dataMap" :key="index"
            :location="data.location" :url="data.url" :mapId="data.mapId"/>
    </div>
</template>

<script>
    // @ is an alias to /src
    import CustomMap from '@/components/CustomMap.vue';

    export default {
        name: 'MyMaps',
        components: {
            CustomMap,
        },
        data() {
            return {
                dataMap: [
                    {
                        location: 'Navalperal',
                        mapId: 'map_01',
                        url: 'tracks/las-acebeas-navalperal-sierra-de-segura-.gpx',
                    },
                    {
                        location: 'El Batrocal',
                        mapId: 'map_02',
                        url: 'tracks/el-real-de-la-jara-camino-batrocal.gpx',
                    },
                    {
                        location: 'Fuenteheridos y Galaroza',
                        mapId: 'map_03',
                        url: 'tracks/colores-de-otono-por-fuenteheridos-y-galaroza.gpx',
                    },
                    {
                        location: 'Nacimiento Río Cuervo - Muela de San Felipe',
                        mapId: 'map_04',
                        url: 'tracks/nacimiento-rio-cuervo-san-felipe-cima.gpx',
                    },
                    {
                        location: 'Ascenso a la poza del Trabuquete',
                        mapId: 'map_05',
                        url: 'tracks/ascenso-a-la-poza-del-trabuquete.gpx',
                    }
                ]
            }
        },
    }
</script>