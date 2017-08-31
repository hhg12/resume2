<template>
  <div id="preview">
    <section>
      <h1>{{resume.profile.name}}</h1>
      <p>{{resume.profile.city}} |  {{resume.profile.title}}</p>
      <hr>
    </section>
    <section v-if="filter(resume.work).length > 0">
      <h2>工作经历</h2>
     <ul>
       <li v-for="item in filter(resume.work)" v-bind:key="item">
         {{item.company}}
         <hr>
         {{item.content}}
       </li>
     </ul>
    </section>
    <section v-if="filter(resume.study).length > 0">
      <h2>学习经历</h2>
      <ul>
        <li v-for="item in filter(resume.study)" v-bind:key="item">
          {{item.school}} -
          {{item.degree}} -
          {{item.time}}
        </li>
      </ul>
    </section>
    <section v-if="filter(resume.projects).length > 0">
      <h2>项目经历</h2>
      <ul>
        <li v-for="item in filter(resume.projects)" v-bind:key="item">
          {{item.name}}
          <hr>
          {{item.project}}
        </li>
      </ul>
    </section>
    <section v-if="filter(resume.awards).length > 0">
      <h2>获奖情况</h2>
      <ul>
        <li v-for="item in filter(resume.awards)" v-bind:key="item">
          {{item.name}}
        </li>
      </ul>
    </section>
    <section v-if="filter(resume.contacts).length > 0">
      <h2>获奖情况</h2>
      <ul>
        <li v-for="item in filter(resume.contacts)" v-bind:key="item">
          QQ-{{item.qq}} <br>
          Wechat-{{item.wechat}} <br>
          Email-{{item.email}} <br>
          Phone-{{item.phone}}
        </li>
      </ul>
    </section>

  </div>
  
</template>

<script>
export default {
  name: 'Preview',
  props: ['resume'],
  methods: {
    filter(array){          //剔除value全为空的对象
      let _this = this
      return array.filter(function(item){
        return !_this.isEmpty(item)
      })
    },
    isEmpty(object){        //只要一个value不为空，就返回true
      let empty = true
      for(let key in object){
        if(object[key]){
          empty = false
          break
        }
      }
      return empty
    }
  },
}
</script>

<style lang="scss">
#preview{
  overflow: auto;
  min-height: 100px;
  background: #fff;
  box-shadow: 0 1px 3px 0 rgba(0,0,0,0.25);
  section {
    margin: 32px 24px;
    font-size: 16px;
    h2 {
      display: inline-block;
      font-size: 24px;
      padding: 10px 10px;
      background: #00b38a;
      color: white;
      margin-bottom: 10px;
    }
  }
}
</style>
