<template>
  <div class="end">
    <h3>请确认预约信息</h3>
    <ul>
      <li>预约科室：{{headList.depatment}}</li>
      <li>预约日期：{{headList.date}}</li>
      <li>预约医生：{{headList.doctor}}</li>
      <li>预约时间：{{headList.times}}</li>
    </ul>
    <div class="button">
      <el-button type="primary">确认预约</el-button>
    </div>
  </div>
</template>

<script>
export default {
  name: "end",
  props: {
    headList: Object
  }
};
</script>

<style scoped lang="less">
ul {
  padding-left: 300px;
  line-height: 40px;
}
h3 {
  height: 60px;
  line-height: 60px;
  text-align: center;
}
.button {
  margin-top: 30px;
  text-align: center;
}
</style>

