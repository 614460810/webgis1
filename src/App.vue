<template>
  <div id="app">
    <el-container class="app-out-pannel">
      <el-header class="sys-header">一张图项目系统</el-header>
      <el-container class="app-content-pannel">
        <el-aside width="200px" class="sys-menu">
          <el-menu default-active="1" class="el-menu-vertical-demo" background-color="aqua"  text-color="#fff" @select='handleMenuSelect'>
            <el-menu-item index="1">
              <i class="el-icon-monitor"></i>
              <!-- <span slot="title">首页大屏</span> -->
            </el-menu-item>
            <el-menu-item index="2">
              <i class="el-icon-picture-outline"></i>
              <!-- <span slot="title">一张图</span> -->
            </el-menu-item>
          </el-menu>
        </el-aside>
        <el-main class="sys-content">
         
          <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>

  </div>
</template>

<script>
// import { METHODS } from 'http';

// import router from './router/router';

export default {
  name: 'App',
  data() {

  },
  components: {
   
    
},
  methods:{
    handleMenuSelect(index){
      if(index==='1'){
        this.$router.push('/');

      }else if (index==='2'){
        this.$router.push('/onemap');

      }
    },
  }
}
</script>

<style>
html,
body,
#app {
  position: relative;
  width: 100%;
  height: 100%;
  margin: 0;
}

.app-out-pannel,
.app-content-pannel {
  height: 100%;
}

.sys-menu {
  background-color: aqua;
  width: 64px !important;

}

.sys-header {
  background-color: bisque;
  line-height: 60px;
}

.sys-content {
  padding: 5px !important;
}
</style>
