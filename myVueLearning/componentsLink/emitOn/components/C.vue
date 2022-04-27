<template>
  <div id="C">
    <h3>C组件：{{title}}，{{title2}}</h3>
  </div>
</template>

<script>
export default {
  name: "C",
  data() {
    return {
      title: "",
      title2: ""
    }
  },

  //在模板编译完成后执行
  mounted() {
    console.log("c")
    this.$on('data-a', title => {
      // 箭头函数内部不会产生新的this，这边如果不用=>,this指代Event
      // console.log("此处的this是：", this);
      this.title = title;
    })
    this.$on('data-b', title2 => {
      this.title2 = title2;
    })
  }
}
</script>

<style scoped>

</style>
