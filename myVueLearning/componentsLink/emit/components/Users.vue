<template>
  <div id="user">
    <!-- 绑定一个点击事件 -->
    <h1 @click="changeTitle">{{title}}</h1>
  </div>
</template>

<script>
export default {
  name: "Users",
  data() {
    return {
      title: "Vue.js Demo"
    }
  },
  methods: {
    changeTitle() {
      // 自定义事件，传递值“子组件向父组件传递值”
      this.$emit("titleChanged", "子组件向父组件传递值");
    }
  }
}
</script>

<style scoped>
  #user{
    height: 50px;
    width: 100%;
    background-color: #5bc0de;
    font-size: 20px;
  }
</style>
