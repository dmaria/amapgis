<template>
  <div id="mapview">
      
  </div>
</template>

<script>
import { loadModules } from "esri-loader";
const options={
    url:'https://js.arcgis.com/4.22/init.js',
    css:'https://js.arcgis.com/4.22/esri/themes/light/main.css'
};
export default {
    name:"mapview",
    mounted:function () {
        this._createMapView();
    },
    methods:{
        async _createMapView(){
            console.log('_createMapView');
            const [Map,MapView]=await loadModules(
                ['esri/Map','esri/views/MapView'],
                options
            )

            const map = new Map({
                basemap:'osm',
            })

            const view = new MapView({
                container:'mapview',
                map:map,
                zoom:11,
                center:[113.401145,22.517239]
            })

            view.ui.components=[];//去掉左上角缩放
        }
    }
}
</script>

<style>
#mapview{
    position: relative;
    width: 100%;
    height: 100%;
}
</style>