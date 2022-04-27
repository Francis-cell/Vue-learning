<template>
  <div id="A">
    <h3>A组件：{{title}}</h3>
    <button @click="send">将数据发送给主组件</button>
  </div>
</template>

<script>
export default {
  name: "A",
  data() {
    return {
      title: 'A组件消息'
    }
  },
  methods: {
    send() {
      this.$emit('data-a', this.title);
    }
  }
}
</script>

<style scoped>

</style>
