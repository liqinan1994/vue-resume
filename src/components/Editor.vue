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
				<profileEditor v-bind:profile="profile" />
			</li>

            <!-- 工作经历 -->
			<li v-bind:class="{active:currentTab === 1}">
                <workHistoryEditor v-bind:workHistory="workHistory" />
			</li>
			<li v-bind:class="{active:currentTab === 2}">
				<h2>学习经历</h2>
			</li>
			<li v-bind:class="{active:currentTab === 3}">
				<h2>个人项目</h2>
			</li>
			<li v-bind:class="{active:currentTab === 4}">
				<h2>获奖经历</h2>
			</li>
			<li v-bind:class="{active:currentTab === 5}">
				<h2>联系方式</h2>
			</li>
		</ol>

	</div>
</template>

<script>
    import profileEditor from './profileEditor'
    import workHistoryEditor from './workHistoryEditor'
	export default {
		components: {
			profileEditor,workHistoryEditor
		},
		data(){
			return {
				currentTab: 0,
				icons: ['cardid','work1','book','heart','jiangbei1','phone'],
				profile: {
					name: '',
					city: '',
					birth: ''
				},
				workHistory: [
                    {company: '', content: ''}
				]
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