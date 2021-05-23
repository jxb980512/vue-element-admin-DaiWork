<template>
  <!-- <el-container class="bg">
        <dv-loading>
          <div class="loading">
          {{message}}
          </div>          
        </dv-loading>
  </el-container> -->
  <div v-loading="loading" 
  :element-loading-text="message"
  class="bg">
    <el-row :gutter="20" style="margin-right: 0px">
      <el-col :span="6" :offset="16">
        <div class="grid-content bg-purple">
          <el-form ref="form" :model="form" label-width="100px">
             <el-form-item style="margin-left:0px">
               <h1 style="margin-left:10%">系统名称</h1>
             </el-form-item>
            <el-form-item label="利用率选择">
              <el-checkbox
                :indeterminate="isIndeterminate"
                v-model="checkAll"
                @change="handleCheckAllChange"
                >全选</el-checkbox
              >
              <div style="margin: 15px 0"></div>
              <el-checkbox-group
                v-model="checkedCities"
                @change="handleCheckedCitiesChange"
              >
                <el-checkbox v-for="city in cities" :label="city" :key="city">{{
                  city
                }}</el-checkbox>
              </el-checkbox-group>
            </el-form-item>
            <el-form-item label="策略选择">
              <el-select v-model="form.way" placeholder="请选择策略" multiple>
                <el-option label="BFD" value="a"></el-option>
                <el-option label="Default" value="b"></el-option>
                <el-option label="Random" value="c"></el-option>
                <el-option label="CE-Storm" value="d"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" @click="onSubmit">立即加载</el-button>
            </el-form-item>
          </el-form>
        </div>
      </el-col>
    </el-row>    
  </div>
</template>
<script>
export default {
  data() {
    return {
      checkAll: false,
      checkedCities: [],
      cities: ['10MB/S','20MB/S','30MB/S'],
      isIndeterminate: true,
      form: {
        use: [],
        way: [],
      },
      value: [],
      message: "正在初始化模板...",
      loginForm: {
        username: "admin",
        password: "111111",
      },
      login: {},
      loading: false
    };
  },
  mounted() {
  },
  methods: {
     handleCheckAllChange(val) {
        this.checkedCities = val ? this.cities : [];
        this.isIndeterminate = false;
      },
       handleCheckedCitiesChange(value) {
        let checkedCount = value.length;
        this.checkAll = checkedCount === this.cities.length;
        this.isIndeterminate = checkedCount > 0 && checkedCount < this.cities.length;
      },
    loadShow() {
      setTimeout(() => {
        this.message = "正在加载数据...";
      }, 2000),
        setTimeout(() => {
          this.message = "正在渲染模块...";
        }, 4000);
      setTimeout(() => {
        this.message = "已完成";
        this.toHome();
      }, 5000);
    },
    toHome() {
      this.$store
        .dispatch("user/login", this.loginForm)
        .then(() => {
          this.$router.push({
            path: this.redirect || "/",
            query: this.otherQuery,
          });
        })
        .catch(() => {});
    },
    onSubmit(){
      console.log("1")
      this.loading=true
      this.loadShow()
    }
  },
};
</script>

<style scoped>
.bg {
  width: 100%;
  height: 100%;
  background-color: rgba(255, 255, 255, 0.89);
}
.loading {
  margin-top: 60px;
  color: aliceblue;
  font-size: 30px;
  
}
.grid-content {
  border-radius: 4px;
  min-height: 36px;
  margin-top: 40%;
}
.bg-purple {
  background: #d3dce6;
}
</style>