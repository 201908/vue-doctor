<template>
  <div class="times">
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
  name: "times",
  props: {
    list: Array
  },
  data() {
    return {
      num: -1
    };
  },
  methods: {
    current(index) {
      this.num = index;
    }
  }
};
</script>

<style scoped lang="less">
</style>
