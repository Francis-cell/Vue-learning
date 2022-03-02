<template>
  <div>
    <ul>
      <li v-for="n in lists">{{n}}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App.vue",
  data() {
    return {
      lists:[1,2,3,4]
    }
  }
}
</script>

<style scoped>

</style>
