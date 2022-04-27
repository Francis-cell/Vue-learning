<template>
  <div class="border" id="child2">
    <p>boo: {{ boo }}</p>
    <p>childCom2: {{ $attrs }}</p>
    <childCom3 v-bind="$attrs"></childCom3>
  </div>
</template>
<script>
import childCom3 from "./childCom3";
export default {
  components: {
    childCom3
  },
  // inheritAttrs: false,
  props: {
    boo: String
  },
  created() {
    console.log(this.$attrs);
  }
};
</script>
<style scoped>
 #child2{
   background-color: #ce8483;
   width: 80%;
   height: 80px;
 }
</style>
