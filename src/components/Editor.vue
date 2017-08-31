<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="i in [0,1,2,3,4,5]"
           v-bind:class="{active:selected===i}"
          @click="selected=i" v-bind:key="i">
          <svg class="icon" aria-hidden="true">
            <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
          </svg>
        </li>
      </ol>
    </nav>
    <ol class="panels">
      <li :class="{active: selected === 0}">
         <ProfileEditor v-bind:profile="resume.profile"/> 
      </li>
      <li :class="{active: selected === 1}">
         <ArrayEditor v-bind:items="resume.work" v-bind:lables="{company: '公司', content:
         '工作内容'}" title="工作经历"/> 
      </li>
      <li :class="{active: selected === 2}">
        <ArrayEditor v-bind:items="resume.study" v-bind:lables="{school: '学校', degree:
        '学位', time: '时间'}" title="学习经历"/> 
      </li>
      <li :class="{active: selected === 3}">
        <ArrayEditor v-bind:items="resume.projects" v-bind:lables="{name: '项目名称',
        project: '工作内容'}" title="项目经历"/> 
      </li>
      <li :class="{active: selected === 4}">
        <ArrayEditor v-bind:items="resume.awards" v-bind:lables="{name: '获奖详情'}" 
        title="获奖情况"/> 
      </li>
      <li :class="{active: selected === 5}">
        <h2>联系方式</h2>
        <el-form >
        <el-form-item label="QQ">
          <el-input v-model="resume.contacts[0].qq"></el-input>
        </el-form-item>
        <el-form-item label="微信">
          <el-input v-model="resume.contacts[0].wechat"></el-input>
        </el-form-item>
        <el-form-item label="邮箱">
          <el-input v-model="resume.contacts[0].email"></el-input>
        </el-form-item>
        <el-form-item label="手机">
          <el-input v-model="resume.contacts[0].phone"></el-input>
        </el-form-item>
      </el-form> 
      </li>
         
    </ol>
  </div>
</template>

<script>
import ProfileEditor from './ProfileEditor'
import ArrayEditor from './ArrayEditor'
export default {
  name: 'Editor',
  props : ['resume'],
  components: {
    ProfileEditor,ArrayEditor
  },
  data: function(){
    return {
      selected: 0,
      icons: ['shenfenzhengzhengjian', 'gongsi', 'book', 'xin', 'jiangbei01', '3-copy'],
      
    }
  },
  methods: {
    
  }
}
</script>

<style lang="scss">
.icon {
    width: 24px; height: 24px;
    fill: white;
}
#editor {
  color: black;
  min-height: 100px;
  background: #fff;
  box-shadow: 0 1px 3px 0 rgba(0,0,0,0.25);
  display: flex;
  > nav {
    background: black;
    width: 80px;
    > ol > li {
      padding: 8px 0;
      text-align: center;
      &.active {
        background: white;
        > .icon {
          fill: black;
        }
      }
    }
  }
  .panels{
    flex: 1;
    li{
      display: none;
      padding: 24px;
      height: 100%;
      overflow: auto;
      &.active {
        display: block;
      }
      
    }
  }
}

</style>

