<template>
	<div id="Preview">
		<section>
			<h1>{{resume.profile.name || '请填写姓名'}}</h1>
			<p>{{resume.profile.city || '请填写城市'}} | {{resume.profile.birth || '请填写出生年月'}}</p>	
	    </section>

		
         <section v-if="filter(resume.workHistory).length > 0">
			<h2>工作经历</h2>
			<ul v-for="work in filter(resume.workHistory)">
				<li>{{work.duration || '工作起始时间'}}</li>
				<li>
					<span>{{work.company}}</span>
					<span>{{work.content}}</span>
				</li>
			</ul>
			<hr>
		</section>

		<section v-if="filter(resume.studyHistory).length > 0">
			<h2>学习经历</h2>
			<ul v-for="study in filter(resume.studyHistory)">
				<li>{{study.duration || '起始时间'}}</li>
				<li>
					<span>{{study.school || '学校名称'}}</span>
					<span>{{study.degree || '学位'}}</span>

				</li>
			</ul>
		</section>

		<section v-if="filter(resume.projects).length > 0">
			<h2>项目</h2>
			<ul v-for="project in filter(resume.projects)">
				<li>{{project.name || '项目名称'}}</li>
				<li>{{project.content || '内容'}}</li>
			</ul>
		</section>	

	    <section v-if="filter(resume.awards).length > 0 ">
	      <h2>获奖情况</h2>
	      <ul v-for="award in filter(resume.awards)">
	        <li>{{award.name ||'奖项名称'}}</li>
	        <li>{{award.content ||'获奖情况'}}</li>
	      </ul>
	    </section>		

		<section>
	      <h2>联系方式</h2>
	      <ul>
	      	<li>{{resume.contacts.qq || 'QQ'}}</li>
	      	<li>{{resume.contacts.wechat || '微信'}}</li>
	        <li>{{resume.contacts.email || '邮箱'}}</li>
	        <li>{{resume.contacts.phone || '手机'}}</li>
	        <li></li>
	      </ul>
	    </section>	
	</div>
</template>

<script>
	export default {
		props: ['resume'],
		methods:{
			filter(array){ //找出非空对象
				return array.filter(item=> !this.isEmpty(item))
			},
			isEmpty(object){  //只要有一个 value 不是 false 就返回 false
				let empty = true
				for(let key in object){
					if(object[key]){
						empty = false
						break
					}
				}
				return empty
			}
		}
	}
</script>

<style lang='scss'>
	#Preview {
        padding: 32px;
        overflow: auto;
        >section {
        	overflow: auto;
        	>h1 {
		        border-bottom: 2px solid #3fa5b6;
		        color: #5bafd8;
		        font-size: 30px;
		        margin-bottom: 10px;        		
        	}
        	>h2 {
        		color: #5bafd8;
		        text-align: left;
		        background: rgba(0, 0, 0, 0.1);
		        border-left: 3px solid #000;
		        padding-left: 4px;
		        margin: 20px 0 10px 0;
		        padding: 5px;
        	}
        	>ul {
        		padding: 8px;
        		display: flex;
        		>li {
        			flex: 1;
        		}
        	}
        	>li:nth-child(1) {
        		flex-grow: 2;
        		align-self: center;
        	}
	        >li:nth-child(2) {
	          text-align: left;
	          flex-grow: 4;
	          display: flex;
	          flex-direction: column;
	        }
        }

	}
</style>