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
        profile: { name: '郭浩',profession: 'Software Engineer',about: '热爱接触和学习新鲜事物，对一切充满好奇，喜欢探讨各种各样跟web有关的的奇技淫巧'},
        work: [{company: '研究所', position: 'CEO/President', startDate: '2014-04-23',
        endDate: '2015-06-30', content: '东云研究所是一所专业的高级的智能机器人研究机构，志在于使机器人更加智能化，造价更低，外观更美，更实用。'}],
        education: [{school: '学校', degree: '研究生', startDate: '2011-04-05', endDate:
        '2014-04-22',area: '安徽'}],
        projects: [{name: '项目名称', project: '个人博客网站，实现了注册登录，增删改除博客，并对博客进行分类的功能.用户可以对博客进行评论，并且在留言板留言，博主可以对这些评论进行回复',
        startDate: '2014-08-01',endDate: '2014-08-31'}],
        awards: [{name: '获奖情况', date:'2016-05-04', address:'安徽合肥', 
        summary: '在研究寝室温度与学习的三位曲线上做了比较大的贡献，提出了没有空调学不动，上课总是在五楼太坑爹，不吹风扇写不出代码等重要理论。'}],
        contacts: [{ email: 'hdgd@gmail.com', phone: '手机',github: '12', address: '安徽合肥'}]
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
.previewMode main {
  margin: 0;
  padding: 0;
}
.previewMode #topbar {
  display: none;
}
.previewMode #editor {
  display: none;
}
.previewMode #preview {
  margin: 0;
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
