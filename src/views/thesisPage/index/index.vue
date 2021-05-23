<template>
  <el-container>
    <el-main>
      <VueClock />
      <el-calendar v-model="value"> </el-calendar>
    </el-main>
  </el-container>
</template>
<script>
import VueClock from "@dangvanthanh/vue-clock";
export default {
  components: { VueClock },
  data() {
    return {
      value: new Date()
    };
  },
};
</script>

<style scoped>
.el-container {
  position: relative;
  height: calc(100vh - 84px);
}
</style>