<template>
	<div id="Editor">
		<nav>
			<ol>
				<li v-for="i in [0,1,2,3,4,5]"
                    v-bind:class="{active:currentTab === i}"
                    v-on:click="currentTab = i">
					<svg class="icon">
                       <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
                    </svg> 
                </li>                       		
			</ol>
		</nav>

		<ol class="panels">
			<!-- 个人信息 -->
			<li v-bind:class="{active:currentTab === 0}">
				<profileEditor v-bind:profile="resume.profile" />
			</li>

            <!-- 工作经历 -->
			<li v-bind:class="{active:currentTab === 1}">
                <arrayEditor v-bind:items="resume.workHistory" v-bind:labels="{company:'公司',content:'工作内容'}" title="工作经历" />
			</li>

			<!-- 学习经历 -->
			<li v-bind:class="{active:currentTab === 2}">
				<arrayEditor v-bind:items="resume.studyHistory" v-bind:labels="{school:'学校',degree:'学历',duration:'时间'}" title="学习经历" />
			</li>

			<!-- 项目经历 -->
			<li v-bind:class="{active:currentTab === 3}">
				<arrayEditor v-bind:items="resume.projects" v-bind:labels="{name:'项目名称',content:'项目内容'}" title="项目经历" />
			</li>
			<li v-bind:class="{active:currentTab === 4}">
				<arrayEditor v-bind:items="resume.awards" v-bind:labels="{name:'奖励详情',content:'工作内容'}" title="获奖情况" />
			</li>
			<li v-bind:class="{active:currentTab === 5}">
				<h2>联系方式</h2>
				<el-form>
					<el-form-item label="QQ">
					    <el-input v-model="resume.contacts.qq" ></el-input>
					</el-form-item>
					<el-form-item label="微信">
					    <el-input v-model="resume.contacts.wechat"></el-input>
					</el-form-item>
					<el-form-item label="邮箱">
					    <el-input v-model="resume.contacts.email"></el-input>
					</el-form-item>
					<el-form-item label="手机">
					    <el-input v-model="resume.contacts.phone"></el-input>
					</el-form-item>
			    </el-form>
			</li>
		</ol>

	</div>
</template>

<script>
    import profileEditor from './profileEditor'
    import arrayEditor from './arrayEditor'
    import Preview from './Preview'
	export default {
		components: {
			profileEditor,arrayEditor,Preview
		},
		props: ['resume'],
		data(){
			return {
				currentTab: 0,
				icons: ['cardid','work1','book','heart','jiangbei1','phone'],
			}
		},
		created(){
		}
	}
</script>

<style lang="scss">
	#Editor {
		display: flex;
		min-height: 100px;
		> nav {
			width: 80px;
			background: #000;
			> ol > li {
				padding: 8px 0;
				text-align: center;
				> .icon {
					width: 24px;
					height: 24px;
					fill: #fff;	
				}
				&.active {
					background: #fff;
					> .icon {
						fill: #000;
					}
				}
		    }
		}
		> .panels {
			flex: 1;
			> li {
				display: none;
				padding: 32px;
				overflow: auto;
				height: 100%; //待查
				&.active {
				   display: block;

			    }
			}
			.container {
				position: relative;
				> .el-icon-delete {
					position: absolute;
					right: 0; top: 0;		
				}

			}
		}
	}
</style>