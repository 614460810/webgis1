<template>
    <div class="maptools-view">
        <span class="maptools-item">行政区导航</span>
        <span class="maptools-item">目录树管理</span>
        <span class="maptools-item">距离测量</span>
        <span class="maptools-item">面积测量</span>
        <span class="maptools-item">清屏</span>
        

    </div>
</template>

<script>

export default {
    name: 'MapTools',
    components: {

    },
    
    methods: {
        
    }
}
</script>

<style>
html,
body {
    position: relative;
    width: 100%;
    height: 100%;
    margin: 0;
}
.maptools-view{
    position: absolute;
    top: 10px;
    right: 20px;
    height: 40px;
   
    background-color: aliceblue;
    line-height: 40px;
    padding: 0 15px;
}
.maptools-item{
    padding-left: 10px;
    cursor: pointer;
}
.maptools-item:first-child{
    padding-left: 0;
    
}
</style>
