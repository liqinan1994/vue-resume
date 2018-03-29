<template>
  <div id="app" v-bind:class="{previewMode : previewMode}">
    <Login id="login" v-bind:class="{loginMode:loginMode}" v-on:exit="exit"/>
    <Topbar class="topbar" v-on:preview="preview" v-on:login="login"/>
    <main>
      <Editor v-bind:resume="resume" class="editor" />
      <Preview v-bind:resume="resume" class="preview" />
    </main>
    <el-button id="exitPreview" v-on:click="exitPreview">退出预览</el-button>

  </div>
</template>

<script>
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'
import Login from './components/Login'
export default {
  name: 'App',
  components: {
    Topbar,Editor,Preview,Login
  },
  data(){
    return {
      loginMode: false,
      previewMode:false,
      resume: {
        profile: {
          name: '',
          city: '',
          birth: ''
        },
        workHistory: [
          {duration:'', company: '', content: ''}
        ],
        studyHistory: [
          {school: '',degree: '',duration: ''}
        ],
        projects: [
          {name: '',content: ''}
        ],
        awards: [
          {name: '',content: ''}
        ],
        contacts: {
          qq: '',
          wechat: '',
          email: '',
          phone: ''
        }
      }
    }    
  },
  methods: {
    login(){
      this.loginMode = true
    },
    exit(){
      this.loginMode = false
    },
    preview(){
      this.previewMode = true
    },
    exitPreview(){
      this.previewMode = false
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
  display: flex;
  flex-direction: column;
}

.topbar {
  position: relative;
  z-index: 1;
  box-shadow: 0 0 3px hsla(0,0,0,0.4)
}
.icon {
  width: 1em; height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}

main {
  display: flex;
  flex: 1;
  background: #ddd;
    >.editor {
    width: 40em;
    margin: 16px 8px 16px 16px;
    background: #fff;
    box-shadow: 0 0 3px hsla(0,0,0,0.4);
    border-radius: 4px;
    overflow: auto;
  }
  >.preview {
    flex: 1;
    margin: 16px 16px 16px 8px;
    background: #fff;
    box-shadow: 0 0 3px hsla(0,0,0,0.4);
    border-radius: 4px;
    overflow: hidden;
  }
}

.previewMode > #Topbar {
  display: none;
}
.previewMode > main > #Editor {
  display: none;
}
.previewMode > main > #Preview {
  max-width: 800px;
  margin: 16px auto;
}

#exitPreview {
  display: none;
}
.previewMode > #exitPreview {
  display: inline-block;
  position: fixed;
  right: 16px;
  bottom: 16px;
}

#login {
  display: none;
  background: #fff;
  border-radius: 16px;
  box-shadow: 0px 0px 2px 2px hsla(0, 0, 0, 0.3);
  width: 400px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
}
#app>.loginMode {
  display: block;
}

</style>
