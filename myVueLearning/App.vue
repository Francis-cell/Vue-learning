<template>
  <div>
    <h2>测试</h2>
    <childCom1
        :foo="foo"
        :boo="boo"
        :coo="coo"
        :doo="doo"
        title="好的"
    ></childCom1>
  </div>
</template>

<script>
import childCom1 from "./componentsLink/attrListeners/components/childCom1";

export default {
  components: { childCom1 },
  data() {
    return {
      foo: "Javascript",
      boo: "Html",
      coo: "CSS",
      doo: "Vue"
    };
  }
}
</script>
<style scoped>

</style>
