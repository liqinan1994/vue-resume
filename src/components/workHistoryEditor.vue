<template>
	<div>
		<h2>工作经历</h2>
		<el-form>
			<div class="container" v-for="(work,index) in workHistory">
   			  <el-form-item label="公司">
			    <el-input v-model="work.company" ></el-input>
			  </el-form-item>		
   			  <el-form-item label="工作内容">
			    <el-input v-model="work.content"></el-input>
			  </el-form-item>
			  <i class="el-icon-delete" v-on:click="removeWorkHistory(index)"></i>
			  <hr style="marginBottom:8px">
			  <el-button type="primary" v-on:click="addWrokHistory">添加经历</el-button>		
			</div>
		</el-form>
	</div>
</template>

<script>
	export default {
		props: ['workHistory'],
		methods: {
            addWrokHistory(){
                this.workHistory.push({
                	company:'',content:''
                })
            },

            removeWorkHistory(index){
            	this.workHistory.splice(index,1)
            }
		}
	}
</script>