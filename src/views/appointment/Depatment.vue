<template>
  <div class="depatment">
    <h3 v-if="show">请选择要预约的科室！</h3>
    <ul class="ul-global">
      <li
        v-for="(item,index) in list"
        :key="index"
        :class="{currentColor: index===num}"
        @click="$emit('click',{value:item}), current(index)"
      >{{item}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "depatment",
  props: {
    list: Array
  },
  data() {
    return {
      num: -1,
      show: true
    };
  },
  methods: {
    current(index) {
      this.num = index;
      this.show = false;
    }
  }
};
</script>

<style scoped lang="less">
h3 {
  height: 60px;
  line-height: 60px;
  text-align: center;
}
</style>
