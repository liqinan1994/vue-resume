<template>
	<div>
		<h2>{{title}}</h2>
		<!-- {{keys}} -->
		<el-form>
			<div class="container" v-for="(item,index) in items" v-bind:key="index">
   			  <el-form-item v-for="key in keys" v-bind:label="labels[key] || key" v-bind:key="key">
			    <el-input v-model="item[key]" ></el-input>
			  </el-form-item>		
			  <i class="el-icon-delete" v-on:click="removeItem(index)"></i>
			  <hr style="marginBottom:8px">
			</div>
			<el-button type="primary" v-on:click="addItem">添加经历</el-button>
		</el-form>
	</div>
</template>

<script>
	export default {
		props: ['items','labels','title'],
		computed: {

			keys(){
				return Object.keys(this.items[0])
			}
		},
		methods: {
            addItem(){
            	const empty = {}

                this.keys.map((key)=>{
                	empty[key] = ''
                })
                this.items.push(empty)
            },

            removeItem(index){
            	this.items.splice(index,1)
            }
		}
	}
</script>