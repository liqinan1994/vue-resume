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
			<li v-for="i in [0,1,2,3,4,5]"
                v-bind:class="{active:currentTab === i}">
                tab {{i}}
			</li>
		</ol>

	</div>
</template>

<script>
	export default {
		data(){
			return {
				currentTab: 0,
				icons: ['cardid','work1','book','heart','jiangbei1','phone']
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
			> li {
				display: none;
				&.active {
				   display: block; 
			    }
			}
		}
	}
</style>