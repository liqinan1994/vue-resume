<template>
    <div id="Topbar">
		<div id="logo">
		    VueResumer
		</div>
		<div class="actions">
			<el-button type="primary" v-on:click="login">登录/注册</el-button>
			<el-button v-on:click="preview">预览</el-button>
		</div>
	</div>
</template>

<script>
	export default {
		methods: {
			preview(){
				// alert(1)
				this.$emit('preview')
			},
			login(){
				this.$emit('login')
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
    > #logo {
      font-family: Century Gothic;
      font-size: 40px;
      font-weight: bold;
      color: #3fa5b6;
      text-shadow: 1px -1px 0 #2e7b87, -1px 2px 1px #737272, -2px 4px 1px #767474, -3px 6px 1px #787777, -4px 8px 1px #7b7a7a;
    }
}
</style>