<template>
  <el-container>
    <el-aside width="200px">
      <el-row>
        <el-col>
          <label>请选择利用率：</label>
        </el-col>
        <el-col>
          <el-select v-model="selectValue" placeholder="请选择">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            >
            </el-option>
          </el-select>
        </el-col>
      </el-row>
    </el-aside>
    <el-main>
      <el-row>
        <el-col :span="12">
          <Chart id="cpu" width="100%" height="100%"></Chart>
        </el-col>
        <el-col :span="12">
          <Chart id="rom" width="100%" height="100%"></Chart> 
        </el-col>
      </el-row>
    </el-main>
  </el-container>
</template>

<script>
import Chart from "./components/index";
export default {
  name:"chatszhu",
  components: { Chart },
  data() {
    return {
     selectValue:"",
      options: [
        {
          value: "one",
          label: "10MB/S",
        },
        {
          value: "two",
          label: "20MB/S",
        },
        {
          value: "three",
          label: "30MB/S",
        },
      ],
    };
  },
  watch: {
    selectValue(newVal,oldVal){
    switch (newVal) {
      case "one":
        break;
      case "two":
        break;
      case "three":
        break;
      default:console.log('数据读取错误！')
        break;
    }
    }
  }
};
</script>

<style scoped>
.el-container {
  position: relative;
  height: calc(100vh - 84px);  
}
.el-col-12{
  position: relative;
  width: 50%;
  height: calc(100vh - 125px);
}
</style>