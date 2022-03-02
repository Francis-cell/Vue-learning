<template>
	<!-- 组件结构代码 -->
	<div class="demo">
		<h3>学校名称：{{schoolName}}</h3>
		<h3>学校地址：{{address}}</h3>
	</div>
</template>

<script>
	// 组件操作执行代码
	export default {
		name: 'School',
		data(){
			return {
				schoolName: '好的大学',
				address: '上海'
			}
		}
	}
</script>

<style>
	/*组件样式代码*/
	.demo{
		background-color: #13E2EBFF;
	}
</style>