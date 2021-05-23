<template>
  <div>
      <el-form>
          <el-form-item label="用户名">
              <el-input v-model="username"></el-input>
          </el-form-item>
          <el-form-item label="密码">
              <el-input v-model="password" show-password ></el-input>
          </el-form-item>
          <el-form-item>
              <el-button @click="login">登录</el-button>
          </el-form-item>
      </el-form>
  </div>
</template>

<script>
export default {
data () {
    return {
        username:"cdadmin",
        password:""
    }
}
}
</script>

<style>

</style>