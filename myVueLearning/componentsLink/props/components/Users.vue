<template>
  <div>
    <h1>{{msg}}</h1>
    <h2>用户姓名：{{name}}</h2>
    <h2>用户年龄：{{age}}</h2>
    <h2>用户性别：{{sex}}</h2>
  </div>
</template>

<script>
export default {
  name: "Users",
  data() {
    return {
      msg: '一个用户的信息',
    }
  },
  // 1、简单声明接收
  // props: ['name','age','sex']

  // 2、接收数据的时候，对数据的类型进行限制
  // props: {
  //   name: String,
  //   age: number,
  //   sex: String,
  // }

  // 3、接收数据的同时，对数据的必要性、数据类型、默认值的限制
  props: {
    name: {
      type: String,
      require: true,
    },
    age: {
      type: Number,
      default: 10,
    },
    sex: {
      type: String,
      require: true,
    }
  }
}
</script>

<style scoped>

</style>
