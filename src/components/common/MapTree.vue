<template>
    <div class="maptree-pannel">
        <el-tree :data="data" :props="defaultProps" @node-click="handleNodeClick"></el-tree>

    </div>
</template>

<script>
import { loadModules } from 'esri-loader';
const options = {
    url: 'https://js.arcgis.com/4.18/init.js',
    css: 'https://js.arcgis.com/4.18/esri/themes/light/main.css',
};


export default {
    name: 'MapTree',
    data() {
        return {
            data: [{
                label: '暖色系',
                layerid: 'layerid',
                layerurl: 'http://map.geoq.cn/arcgis/rest/services/ChinaOnlineStreetWarm/MapServer',
                children: [{
                    label: '二级 1-1',
                    children: [{
                        label: '三级 1-1-1'
                    }]
                }]
            }, {
                label: '一级 2',
                children: [{
                    label: '二级 2-1',
                    children: [{
                        label: '冷色系',
                        layerid: 'layerid',
                        layerurl: 'http://map.geoq.cn/arcgis/rest/services/ChinaOnlineStreetGray/MapServer',
                    }]
                }, {
                    label: '二级 2-2',
                    children: [{
                        label: '三级 2-2-1'
                    }]
                }]
            }, {
                label: '一级 3',
                children: [{
                    label: '二级 3-1',
                    children: [{
                        label: '三级 3-1-1'
                    }]
                }, {
                    label: '二级 3-2',
                    children: [{
                        label: '三级 3-2-1'
                    }]
                }]
            }],
            defaultProps: {
                children: 'children',
                label: 'label'
            }
        };
    },
    methods: {
        async handleNodeClick(data) {
            if (data.layerurl) {
                const view = this.$store.getters._getDefaultMapView;
                // const view = this.$store.getters._getDefualtMapView;
                // 删除已存在图层
                const resultLayer=view.map.findLayerById('layerid')
                if(resultLayer){
                    view.map.remove(resultLayer)
                }

                const [TileLayer] = await loadModules(['esri/layers/TileLayer'], options)
                const layer = new TileLayer({ url: data.layerurl, id: data.layerid });
                view.map.add(layer)
            }

        },


    }
};

</script>

<style>
.maptree-pannel {
    position: absolute;
    top: 10px;
    left: 10px;
    height: 300px;
    width: 100px;
    background-color: #fff;
}
</style>
