<template>
  <div class="container">
    <navbar title="计算距离"></navbar>
    <weex-amap class="map" id="map2017" :sdk-key="keys" :zoom="zoom" :center="pos">
      <weex-amap-marker :position="marker1.position" :title="marker1.title"></weex-amap-marker>
      <weex-amap-marker :position="marker2.position" title="marker2.title"></weex-amap-marker>
    </weex-amap>
    <div class="map-control">
      <text class="title">Methods: getDistanceBetweenMarkers</text> 
      <text class="tips">getDistanceBetweenMarkers，可以获取地图上两个坐标点的巨鹿</text>
      <div @click="getDistance" class="btnbox"><text class="btn" >Get Distance</text></div>
      <text class="distance" v-if="distance">{{distance}}</text>
    </div>
  </div>
</template>

<style scoped> 
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
  .btn{
    margin: 20px;
    padding: 20px;
    background-color: #1ba1e2;
    border-radius: 5px;
    color: #fff; 
    text-align:center;
    cursor: pointer;
    font-size: 28px;
  }
  .distance{
    padding: 5px;
    margin: 20px;
    font-size: 22px;
    background-color: #f1c40f;
    color: #000;
  }
</style>

<script>
  const navbar = require('../include/navbar.vue');
  const Amap = weex.requireModule('amap');
  module.exports = {
    components: {
      navbar
    },
    
    data() {
      return {
        keys: {
          h5:'f4b99dcd51752142ec0f1bdcb9a8ec02',
          ios: '',
          android: 'db6a973159cb0c2639ad02c617a786ae'
        },
        marker1: { 
          position: [116.368904, 39.923423],
          title: '标记点1'
        },
        marker2: {
          position: [116.387271, 39.922501],
          title: '标记点2'
        },
        zoom: 13,
        pos: [116.387271, 39.922501],
        distance: false
      };
    },
    
    methods: {
      getDistance() {
        Amap.getLineDistance(this.marker1.position, this.marker2.position, (res) => {
          if(res.result == 'success') {
            this.distance = '两点相距' + res.data.distance + '米';
          } else {
            console.log('计算失败');
          }
        })    
      }
    }
  }
</script>