<template>
  <div class="myechat">
    <h1>表单测试页</h1>
    <el-button type="primary" @click="toForm">主要按钮</el-button>
    <!-- <div>
      //Echat图
    <Chart height="500px" width="100%"></Chart>
    </div> -->
    <!-- 换皮肤 -->
    <!-- <ThemePicker @change="themeChange"></ThemePicker> -->
  </div>
</template>

<script>
import ThemePicker from "@/components/ThemePicker";
import Chart from "@/components/Charts/Myecharts";
export default {
  components: { Chart,ThemePicker },
  data() {
    return {
      context: "",
    };
  },
  methods:{
    themeChange(val) {
      this.$store.dispatch('settings/changeSetting', {
        key: 'theme',
        value: val
      })
    },
    toForm(){
      this.$router.push({
        path:'/myhome/myhometwo'
      })
    }
  }
};
</script>

<style scoped>
.myechat{
  width: 100%;
  height: 100%;
  margin: 30px;
}
</style>