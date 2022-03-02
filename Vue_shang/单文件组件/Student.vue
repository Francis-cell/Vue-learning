<template>
	<!-- 组件结构代码 -->
	<div class="demo">
		<h3>学生信息： {{studentName}}</h3>
		<h3>学生年龄： {{age}}</h3>
	</div>
</template>

<script>
	// 组件操作执行代码
	export default {
		name: 'Student',
		data(){
			return {
				studentName: '张三',
				age: 18
			}
		}
	};
</script>

<style>
	/*组件样式代码*/
	.demo{
		background-color: #DBBB23FF;
	}
</style>