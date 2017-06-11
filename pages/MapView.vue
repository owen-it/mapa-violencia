<template>
  <v-layout column align-horiz-center>
      <gmap-map
        :center="center"
        :zoom="7"
        style="min-width: 100%; height: 600px;"
      >
        <gmap-marker
          :key="index"
          v-for="(m, index) in markers"
          :position="m.position"
          :clickable="true"
          :draggable="true"
          @click="center=m.position"
        ></gmap-marker>
      </gmap-map>
  </v-layout>
</template>

<script>
  export default {
    data () {
      return {
        center: {lat: 10.0, lng: 10.0},
        markers: [{
          position: {lat: 10.0, lng: 10.0}
        }, {
          position: {lat: 11.0, lng: 11.0}
        }]
      }
    },
    watch: {
      '$route'(to, from) {
        // Call resizePreserveCenter() on all maps 
        Vue.$gmapDefaultResizeBus.$emit('resize')
      }
    }
  }
</script>

<style>
  .vue-map {
    height: 100%;
  }
</style>