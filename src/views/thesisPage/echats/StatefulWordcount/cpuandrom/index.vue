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
          <cpuLine
            id="cpu"
            :tabelData="tabelDataCpu"
            height="100%"
            width="100%"
          ></cpuLine>
        </el-col>
        <el-col :span="12">
         
          <cpuLine
            id="rom"
            :tabelData="tabelDataRom"
            height="100%"
            width="100%"
          ></cpuLine>
      
        </el-col>
      </el-row>
    </el-main>
  </el-container>
</template>

<script>
import cpuLine from "./components/LineChats";
export default {
  name: "stateFul",
  components: { cpuLine },
  data() {
    return {
      selectValue: "",
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
      tabelDataCpu: {
        title: "cpu利用率",
        option: ["一", "二", "三", "四","五"],
        xdata: ["周一", "周二", "周三", "周四", "周五", "周六", "周日"],
        ydata: [
          [120, 132, 101, 134, 90, 230, 210],
          [220, 182, 191, 234, 290, 330, 310],
          [150, 232, 201, 154, 190, 330, 410],
          [320, 332, 301, 334, 390, 330, 320],
          [820, 932, 901, 934, 1290, 1330, 1320],
        ],
      },
      tabelDataRom: {
        title: "ROM利用率",
        option: ["一", "二", "三", "四","五"],
        xdata: ["周一", "周二", "周三", "周四", "周五", "周六", "周日"],
        ydata: [
          [120, 132, 101, 134, 90, 230, 210],
          [220, 182, 191, 234, 290, 330, 310],
          [150, 232, 201, 154, 190, 330, 410],
          [320, 332, 301, 334, 390, 330, 320],
          [820, 932, 901, 934, 1290, 1330, 1320],
        ],
      },
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