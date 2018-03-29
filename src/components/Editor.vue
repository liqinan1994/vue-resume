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
				<profileEditor v-bind:items="resume.profile" v-bind:labels="{name:'姓名',city:'城市',birth:'出生年月'}" v-bind:title="'个人信息'"/>
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
				<arrayEditor v-bind:items="resume.awards" v-bind:labels="{name:'奖项名称',content:'工作内容'}" title="获奖情况" />
			</li>
			<li v-bind:class="{active:currentTab === 5}">
                <profileEditor v-bind:items="resume.contacts" v-bind:labels="{qq:'QQ',wechat:'微信',phone:'手机',email:'邮箱'}" v-bind:title="'联系方式'"/>
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