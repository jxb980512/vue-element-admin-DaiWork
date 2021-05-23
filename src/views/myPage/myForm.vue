<template>
<el-form 
:inline="true" 
ref="form" 
:model="form" 
label-width="100px"
label-position='left'
>
<el-row>
  <el-col :span="6"><div class="grid-content bg-purple">
   <el-form-item label="渠道名称">
    <el-input v-model="form.name"></el-input>
  </el-form-item>  
  </div></el-col>
  <el-col :span="6"><div class="grid-content bg-purple-light">
     <el-form-item label="渠道发起人">
    <el-input v-model="form.people"></el-input>
  </el-form-item>
  </div></el-col>
  <el-col :span="6"><div class="grid-content bg-purple">
   <el-form-item label="渠道日期">
    <el-input v-model="form.date"></el-input>
  </el-form-item>  
  </div></el-col>
  <el-col :span="6"><div class="grid-content bg-purple-light">
   <el-form-item label="渠道内容">
    <el-input v-model="form.context"></el-input>
  </el-form-item>  
  </div></el-col>
</el-row>
<el-row :gutter="20">
  <el-col :span="6">
    <el-form-item label="活动区域">
    <el-select v-model="form.region" placeholder="请选择活动区域">
      <el-option label="区域一" value="shanghai"></el-option>
      <el-option label="区域二" value="beijing"></el-option>
    </el-select>
  </el-form-item>
  </el-col>
<el-col :span="6">
<el-form-item label="渠道变更内容" v-show='channel'>
<el-input placeholder="请输入内容"></el-input>
</el-form-item>
</el-col>
  </el-row>
<el-row>
  <el-col :push="10">
    <el-form-item>
    <el-button type="primary" @click="onSubmit">立即创建</el-button>
    <el-button>取消</el-button>
  </el-form-item>
  </el-col>
</el-row>
</el-form>
</template>

<script>
export default {
  data() {
    return {
      form:{
        name:'',
        people:'',
        date:'',
        context:'',
        region:''
      },
      channel:false
    };
  },
  watch: {
    'form.region'(newVal){
      if(newVal=='beijing'){
        this.channel=true
      }else{
        this.channel=false
      }
    }
  },
  methods: {
    onSubmit() {
      console.log("submit!");
    },
  },
};
</script>

<style scoped>
.myechat {
  width: 100%;
  height: 100%;
  margin: 30px;
}
</style>