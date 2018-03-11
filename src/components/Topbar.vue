<template>
    <div id="Topbar">
		<div id="logo">
		    VueResumer
		</div>
		<div class="actions">
			<el-button type="primary">注册</el-button>
			<el-button>登录</el-button>
		</div>
	</div>
</template>

<style lang="scss">
#Topbar {
	display: flex;
    justify-content: space-between; 
    padding: 16px;
    font-size: 20px;
    align-items: center;
}
</style>