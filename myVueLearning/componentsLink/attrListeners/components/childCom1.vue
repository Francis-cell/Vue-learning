<template class="border">
  <div id="child1">
    <p>foo: {{ foo }}</p>
    <p>childCom1的$attrs: {{ $attrs }}</p>
    <childCom2 v-bind="$attrs"></childCom2>
  </div>
</template>
<script>
import childCom2 from "./childCom2";
export default {
  components: {
    childCom2
  },
  // inheritAttrs: false, // 可以关闭自动挂载到组件根元素上的没有在props声明的属性
  props: {
    foo: String // foo作为props属性绑定
  },
  created() {
    console.log(this.$attrs);
  }
};
</script>
<style scoped>
 #child1{
   background-color: #5bc0de;
   width: 100%;
   height: 100px;
 }
</style>
