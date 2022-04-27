<template>
  <div>
    <h1 @click="changeMsg">{{msg}}</h1>
  </div>
</template>

<script>
export default {
  name: "Users",
  data() {
    return {
      msg: '点击我向父组件传递消息',
    }
  },
  methods: {
    changeMsg() {
      // 自定义事件， 传递值”子组件向父组件传递值“
      this.$emit("msgChanged", "子组件向父组件传递值")
    }
  },
}
</script>

<style scoped>

</style>
