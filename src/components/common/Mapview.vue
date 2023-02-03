<template>
    <div class="mapview-pannel">
        <div id="mapview"></div>
        <div id="basemapToggle"></div>
        <div id="scaleBar"></div>
        <div id="zoom"></div>
    </div>
</template>

<script>
import { loadModules } from 'esri-loader'
import store from '@/store';
// import { container } from 'webpack';
// import { container } from 'webpack';

const options = {
    url: 'https://js.arcgis.com/4.18/init.js',
    css: 'https://js.arcgis.com/4.18/esri/themes/light/main.css',
};

export default {
    name: 'MapView',
    components: {

    },
    mounted: function () {
        this._createMapView();
    },
    methods: {
        async _createMapView() {
            const [Map, MapView, Basemap, TileLayer, BasemapToggle, ScaleBar, Zoom] = await loadModules(['esri/Map', 'esri/views/MapView', 'esri/Basemap', 'esri/layers/TileLayer', 'esri/widgets/BasemapToggle', 'esri/widgets/ScaleBar', 'esri/widgets/Zoom'], options);
            let basemap = new Basemap({
                baseLayers: [
                    new TileLayer({
                        url: "http://map.geoq.cn/arcgis/rest/services/ChinaOnlineStreetPurplishBlue/MapServer",
                        title: "Basemap"
                    })
                ],
                title: "basemap",
                id: "basemap"
            });

            const map = new Map({
                basemap,
            });
            const mapView = new MapView({
                container: 'mapview',
                map,
                zoom: 10,
                center: [119.328892, 26.106859]
            });
            // 地图切换控件
            const basemapToggle = new BasemapToggle({
                view: mapView,
                nextBasemap: "hybrid",
                container: 'basemapToggle'
            })
            mapView.ui.add(basemapToggle)
            // 比例尺
            let scaleBar = new ScaleBar({
                view: mapView,
                unit: 'metric',
                container: 'scaleBar'
            });
            mapView.ui.add(scaleBar)
            // 缩放
            let zoom = new Zoom({
                view: mapView,
                container:'zoom'
            });
            mapView.ui.add(zoom)


           

            mapView.ui.components = [];
            store.commit('_setDefaultMapView', mapView);
        },

    }
}
</script>

<style>
.mapview-pannel,
#mapview {
    position: relative;
    width: 100%;
    height: 100%;
}

#basemapToggle {
    position: absolute;
    bottom: 10px;
    right: 10px;
}

#scaleBar {
    position: absolute;
    bottom: 10px;
    left: 10px;
}
#zoom{
    position: absolute;
    bottom: 100px;
    right: 10px;
}
</style>
