<template>
  <div>
    <Users name="小白" :age="11" sex="女"/>
  </div>
</template>

<script>
import Users from './props/components/Users'

export default {
  name:'App',
  components:{Users}
}
</script>
