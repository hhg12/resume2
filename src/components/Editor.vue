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
        <h2>Contacts</h2>
        <el-form >

        <el-form-item label="email">
          <el-input v-model="resume.contacts[0].email"></el-input>
        </el-form-item>
        <el-form-item label="phone">
          <el-input v-model="resume.contacts[0].phone"></el-input>
        </el-form-item>
        <el-form-item label="github">
          <el-input v-model="resume.contacts[0].github"></el-input>
        </el-form-item>
        <el-form-item label="address">
          <el-input v-model="resume.contacts[0].address"></el-input>
        </el-form-item>
      </el-form> 
      </li>
      <li :class="{active: selected === 2}">
         <ArrayEditor v-bind:items="resume.work" v-bind:lables="{}" title="Work"/> 
      </li>
      <li :class="{active: selected === 3}">
        <ArrayEditor v-bind:items="resume.education" v-bind:lables="{}" title="Education"/> 
      </li>
      <li :class="{active: selected === 4}">
        <ArrayEditor v-bind:items="resume.projects" v-bind:lables="{}" title="Projects"/> 
      </li>
      <li :class="{active: selected === 5}">
        <ArrayEditor v-bind:items="resume.awards" v-bind:lables="{}" title="Awards"/> 
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
      icons: ['shenfenzhengzhengjian','3-copy', 'gongsi', 'book', 'xin', 'jiangbei01', ],
      
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

