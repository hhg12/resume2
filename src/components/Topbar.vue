<template>
  <div id="topbar">
    <div class="wrapper">
      <span class="logo">Resumer</span>
      <div>
        <el-button :disabled="true">注册</el-button>
        <el-button type="primary" :disabled="true">登录</el-button>
        <el-button type="primary" @click="preview" >预览</el-button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'topbar',
  methods: {
    preview(){
      this.$emit('preview')
    }
  }
}
</script>

<style>
#topbar {
  background:#ffffff;
  box-shadow:0 1px 3px 0 rgba(0,0,0,0.25);
  color: red;
  min-height: 64px;
  padding: 0 16px;
}
#topbar > .wrapper {
  min-width: 1024px;
  max-width: 1440px;
  margin: 0 auto;
  height: 64px;
}
#topbar > .wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
#topbar .logo {
  font-size: 24px;
  color: #000;
}
</style>

