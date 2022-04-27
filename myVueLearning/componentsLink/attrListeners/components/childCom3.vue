<template>
  <div class="border" id="child3">
    <p>childCom3: {{ $attrs }}</p>
  </div>
</template>
<script>
export default {
  props: {
    coo: String,
    title: String
  }
};
</script>
<style scoped>
 #child3{
   background-color: #3c763d;
   width: 50%;
   height: 50px;
 }
</style>
