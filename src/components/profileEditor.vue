<template>
<div>
	<h2>{{title}}</h2>
	<el-form>
		<el-form-item v-for="(value,key) in items" v-bind:label="labels[key] || key" v-bind:key="key">
		    <el-input v-model="items[key]" ></el-input>
		</el-form-item>
	</el-form>
</div>
</template>

<script>
	export default {
		props: ['items','labels','title']
	}
</script>