<template>
  <div id="app">
    <!-- 与子组件titleChanged自定义事件保持一致 -->
    <Users v-on:titleChanged="updateTitle"/>
    <h2>{{title}}</h2>
  </div>
</template>

<script>
import Users from './componentsLink/emit/components/Users'

export default {
  name:'App',
  components:{Users},
  data() {
    return{
      title: "传递的是一个值"
    }
  },
  methods: {
    updateTitle(e) {
      // 声明这个函数
      this.title = e;
    }
  }
}
</script>
