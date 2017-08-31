<template>
  <div id="app" v-bind:class="{previewMode: previewMode}">
    <div class="page">
      <header>
        <Topbar v-on:preview="preview"/>    
      </header>  
      <main>
        <Editor v-bind:resume="resume"/>
        <Preview v-bind:resume="resume"/>
      </main>

    </div>
    <el-button id="exitPreview" @click="exitPreview">退出预览</el-button>
  </div>
</template>

<script >
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'

export default {
  name: 'App',
  components: {     //当前目录下的组件
    Topbar,Editor,Preview
  },
  data: function(){
    return {
      previewMode: false,
      text: '你好',
      resume: {
        profile: { name: '郭浩',city: '合肥',title: '1990'},
        work: [{company: '公司', content: '工作内容'},
        ],
        study: [{school: '学校', degree: '学位', time: '时间'}
        ],
        projects: [{name: '项目名称', project: '描述'}
        ],
        awards: [{name: '获奖情况'}
        ],
        contacts: [{qq: 'qq', wechat: '微信', email: '邮件', phone: '手机'}]
      },
    }
  },
  methods: {
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
.page {
  min-width: 1024px;
  max-width: 1440px;
  display: flex;
  flex-direction: column;
  height: 100vh;
  background: #EAEBEC;
  > main {
    display: flex;
    flex: 1;
    justify-content: space-between;
    margin-top: 16px;
    margin-bottom: 16px;
    padding: 0 16px;
    align-self: center;
    width: 100%;
  }
}

#editor {
  width: 32em;
}
#preview {
  flex: 1;
  margin-left: 16px;
}
.previewMode #topbar {
  display: none;
}
.previewMode #editor {
  display: none;
}
.previewMode #preview {
  max-width: 800px;
  margin: 32px auto;
}
#exitPreview {
  display: none;
}
.previewMode #exitPreview {
  display: block;
  position: fixed;
  bottom: 16px;
  right: 16px;
}
</style>
