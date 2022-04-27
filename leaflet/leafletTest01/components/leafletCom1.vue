<template>
  <div id="com1">
    <p>{{mapValue}}</p>
    <button @click="leafletMapTest"></button>
  </div>
</template>

<script>
import leaflet from '../../leafletSource/leaflet';

export default {
  name: "leafletCom1",
  data() {
    return {
      mapValue: ""
    }
  },
  methods: {
    leafletMapTest() {
      var map = leaflet.Map('map', {
        center: [51.505, -0.09],
        zoom: 13
      });
      return map;
    }
  }
}
</script>

<style scoped>

</style>
