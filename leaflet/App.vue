<template>
  <div id="app">
    <leaflet-com1/>
  </div>
</template>

<script>
import leafletCom1 from "./leafletTest01/components/leafletCom1";

export default {
  name: 'App',
  components: {leafletCom1}
}
</script>

<style>
 #app{
   background-color: #5daad4;
 }
</style>
