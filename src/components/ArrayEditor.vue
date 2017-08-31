<template>
  <div>
    <h2>{{title}}</h2>
    <div class="content" v-for="(item, index) in items" v-bind:key="index">
      <el-form >
        <el-form-item v-for="(value, key) in item" v-bind:label="lables[key] || key" v-bind:key="key">
          <el-input v-model="item[key]"></el-input>
        </el-form-item>
      </el-form>
      <hr>
      <el-button type="primary" @click="addWork">增加</el-button>
      <i class="el-icon-circle-close" @click="removeWork(index)"></i>
    </div>
  </div>
</template>
<script>
export default {
  props: [
    'items', 'lables', 'title'
  ],
  methods: {
    keys: function(){
      return Object.keys(this.items[0])
    },
    addWork: function(){
      var empty = {}
      this.keys().map(function(x){
        empty[x] = ''
      })
      this.items.push(empty)
    },
    removeWork: function(index){
      this.items.splice(index,1);
    },
  }
}
</script>
<style lang="scss">
div.content {
  position: relative;
  .el-icon-circle-close {
    position: absolute;
    top: 5px;
    right: 5px;
  }
}
</style>


