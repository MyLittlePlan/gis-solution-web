<template>
  <div id="app">
    <el-switch
      style="position:absolute; right: 10px; top: 10px; z-index: 2"
      v-model="displayModel"
      active-text="二维"
      inactive-text="三维"
    @change="switchModel">
    </el-switch>
    <vl-map :load-tiles-while-animating="true" :load-tiles-while-interacting="true" v-show="displayModel">
      <vl-view :zoom.sync="zoom" :center.sync="center" :rotation.sync="rotation" :max-zoom="maxZoom" :min-zoom="minZoom" :extent="extent"></vl-view>
      <vl-layer-tile id="osm">
        <vl-source-osm></vl-source-osm>
      </vl-layer-tile>
    </vl-map>
    <div class="viewer" v-show="!displayModel">
      <vc-viewer ></vc-viewer>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      displayModel: true,
      zoom: 5,
      center: [106, 34],
      rotation: 0,
      maxZoom: 14,
      minZoom: 3,
      extent: [-180, -90, 180, 90]
    }
  },
  methods: {
    switchModel (model) {
      console.log(model)
    }
  },
  beforeCreate () {
  }
}
</script>

<style>
  html, body, #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
    width: 100%;
    height: 100%;
    margin: 0;
    padding: 0;
}
  .viewer{
    width: 100%;
    height: 100%;
  }
</style>
