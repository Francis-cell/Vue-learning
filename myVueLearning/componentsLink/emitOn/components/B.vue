<template>
  <div id="B">
    <h3>B组件：{{title2}}</h3>
    <button @click="send">将数据发送给主组件</button>
  </div>
</template>

<script>
export default {
  name: "B",
  data() {
    return {
      title2: 'B组件消息'
    }
  },
  methods: {
    send() {
      this.$emit('data-b', this.title2);
    }
  }
}
</script>

<style scoped>

</style>
