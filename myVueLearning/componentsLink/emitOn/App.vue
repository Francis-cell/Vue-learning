<template>
  <div id="app">
    <A/>
    <B/>
    <h3>父组件：{{title}}，{{title2}}</h3>
  </div>
</template>

<script>
import A from './componentsLink/emitOn/components/A'
import B from './componentsLink/emitOn/components/B'

export default {
  name:'App',
  components:{A, B},
  data() {
    return{
      title: "",
      title2: ""
    }
  },

  //在模板编译完成后执行
  mounted() {
    console.log("c")
    this.$on('data-a', title => {
      // 箭头函数内部不会产生新的this，这边如果不用=>,this指代Event
      console.log("此处的this是：", this);
      this.title = title;
    })
    this.$on('data-b', title2 => {
      this.title2 = title2;
    })
  }

}
</script>
