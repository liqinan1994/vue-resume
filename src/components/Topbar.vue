<template>
    <div id="Topbar">
		<div id="logo">
		    VueResumer
		</div>
		<div class="actions">
			<el-button type="primary">注册</el-button>
			<el-button>登录</el-button>
			<el-button v-on:click="preview">预览</el-button>
		</div>
	</div>
</template>

<script>
	export default {
		methods: {
			preview(){
				alert(1)
				this.$emit('preview')
			}
		}
	}
</script>

<style lang="scss">
#Topbar {
	display: flex;
    justify-content: space-between; 
    padding: 16px;
    font-size: 20px;
    align-items: center;
}
</style>