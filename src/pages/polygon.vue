<template>
  <div class="container">
    <navbar title="设置多边形"></navbar>
    <weex-amap class="map" id="map2017" :sdk-key="keys" :zoom="zoom" :center="pos">
      <weex-amap-polygon :path="path" fill-opacity="0.5" fill-color="#2ecc71" fill-width="4"></weex-amap-polygon>
    </weex-amap>
    <div class="map-control">
      <text class="title">Componenet: weex-amap-polygon</text> 
      <text class="tips">weex-amap-polygon 可以在地图上绘制多边形</text>
    </div>
  </div>
</template>

<style>
  .container{
    position: relative;
    flex:1; 
    background-color: #fff;
  }
  .map{
    flex: 1;
    position: relative;
    background-color: #fff;
    min-height: 800px;
    border-bottom-width: 10px;
    border-bottom-color: #fff;
  }
  .map-control{
    padding-top: 20px;
    min-height: 600px;
  }
  .title{
    margin-left: 20px;
    padding-left: 20px;
    padding-top: 10px;
    padding-bottom: 10px;
    font-size: 36px;
    border-left-width: 6px;
    border-left-color: #0f89f5;
    color: #222;
    text-align: left;
  }
  .tips{
    margin: 20px;
    padding: 10px;
    color:#666;
    font-size: 20px;
  }
</style>

<script>
  const navbar = require('../include/navbar.vue');
  var polygonArr = new Array(); //多边形覆盖物节点坐标数组
  polygonArr.push([116.403322, 39.920255]);
  polygonArr.push([116.410703, 39.897555]);
  polygonArr.push([116.402292, 39.892353]);
  polygonArr.push([116.389846, 39.891365]);
  module.exports = {
    components: {
      navbar,
    },
    data() {
      return {
        keys: {
          h5:'f4b99dcd51752142ec0f1bdcb9a8ec02',
          ios: '',
          android: 'db6a973159cb0c2639ad02c617a786ae'
        },
        pos: [116.397428, 39.90923],
        path: polygonArr,
        zoom: 13,
      };
    }
  }
</script>