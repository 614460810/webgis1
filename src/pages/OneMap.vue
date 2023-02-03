<template>
    <div class="onemap-page">
        <Mapview/>
       <MapTools/> 
       <MapTree/> 

    </div>
</template>

<script>
// import MapTree from '@/components/common/MapTree'
import MapTools from '@/components/common/MapTools';
import Mapview from '@/components/common/Mapview.vue';
import MapTree from '@/components/common/MapTree.vue';
// import { loadModules } from 'esri-loader';

export default {
    name: 'OneMap',
   
    components: {
    Mapview,
    MapTools,
    MapTree
},
    methods: {
        
    },
    data () {
        return { }
    }
}
</script>

<style>
.onemap-page {
    position: relative;
    width: 100%;
    height: 100%;
}

</style>
