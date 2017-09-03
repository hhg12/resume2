<template>
  <div>
    <h2>Profile</h2>
    <el-form >
    <el-form-item label="name">
      <el-input v-model="profile.name"></el-input>
    </el-form-item>
    <el-form-item label="profession">
      <el-input v-model="profile.profession"></el-input>
    </el-form-item>
    <el-form-item label="about">
      <el-input v-model="profile.about"></el-input>
    </el-form-item>
  </el-form> 
  </div>
</template>
<script>
export default {
  props: ['profile']
  
}
</script>

