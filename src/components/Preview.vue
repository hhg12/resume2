<template>
  <div id="preview">
    <section class="profile">
      <h1>{{resume.profile.name}}</h1>
      <p>{{resume.profile.profession}}</p>
    </section>
    <main>
    <section class="contacts" v-if="filter(resume.contacts).length > 0">
      <h2>Contacts</h2>
      <ul>
        <li v-for="item in filter(resume.contacts)" v-bind:key="item">
          <ul class="way">
            <li><strong>Github</strong>{{item.github}}</li
            ><li><strong>Email</strong>{{item.email}} </li
            ><li><strong>Phone</strong>{{item.phone}} </li
            ><li><strong>Address</strong>{{item.address}} </li>
          </ul>
        </li>
        <div class="about">
          <strong>About</strong>
          <p>{{resume.profile.about}} </p>
        </div>
      </ul>
    </section>
    <section class="work" v-if="filter(resume.work).length > 0">
      <h2>Work</h2>
      <ul>
        <li v-for="item in filter(resume.work)" v-bind:key="item">
          <strong>{{item.company}}</strong>
          <div class="wrap">
            <div>{{item.position}} </div>
            <div>{{item.startDate}} {{item.endDate}}</div>
          </div>
          <div class="description">{{item.content}}</div>
          
        </li>
      </ul>
    </section>
    <section class="education" v-if="filter(resume.education).length > 0">
      <h2>Education</h2>
      <ul>
        <li v-for="item in filter(resume.education)" v-bind:key="item">
          <div class="wrap">
            <div>{{item.school}}-{{item.area}} </div>
            <div>{{item.startDate}} {{item.endDate}}  </div>
            <div>{{item.degree}} </div>
          </div>
        </li>
      </ul>
    </section>
    <section class="description" v-if="filter(resume.projects).length > 0">
      <h2>Projects</h2>
      <ul>
        <li v-for="item in filter(resume.projects)" v-bind:key="item">
          <div class="wrap">
            <div>{{item.name}}</div>
            <div>{{item.startDate}} {{item.endDate}}  </div>
          </div>
          <div class="description">{{item.project}} </div>
        </li>
      </ul>
    </section>
    <section class="awards" v-if="filter(resume.awards).length > 0">
      <h2>Awards</h2>
      <ul>
        <li v-for="item in filter(resume.awards)" v-bind:key="item">
          <div class="wrap">
            <div>{{item.name}}</div>
            <div>{{item.date}} </div>
            <div>{{item.address}} </div>
          </div>
          <div class="description">{{item.summary}} </div>
        </li>
      </ul>
    </section>
    </main>

    
    

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
    margin-bottom: 10px;
  }
}
#preview .profile {
  background: #00b38a;
  opacity: 0.8;
  padding: 50px;
  margin: 0;
  margin-bottom: 30px;
  color: #f3f3f3;
  h1 {
    margin: 0;
    font-size: 36px;
  }
  p {
    font-size: 16px;
  }
}
#preview .contacts {
  border-top: 1px solid #ccc;
  margin: 16px 0;
  padding: 10px;
  font-size: 16px;
  .way {
    padding: 10px 0;
    li {
      display: inline-block;
      width: 50%;
      padding: 5px 0;
      strong {
        display: inline-block;
        font-size: 16px;
        width: 80px;
      }
    }
  }
  .about {
    strong {
      font-size: 16px;
    }
    p {
      padding: 5px 0;
    }
  }
}
#preview section {
  border-top: 1px solid #ccc;
  margin: 24px 0;
  padding: 10px;
  font-size: 16px;
  h2 {
    padding: 5px 0;
  }
  .wrap div {
    display: inline-block;
    width: 30%;
    margin-top: 10px;
  }
  .description {
    margin-top: 10px;
  }
}
.previewMode #preview main {
  max-width: 850px;
  margin: 0 auto;
}
</style>
