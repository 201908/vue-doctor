<template>
  <div class="depatment">
    <slot></slot>
    <!-- <slot name="other"></slot> -->
    <!-- 具名+作用域 -->
    <!-- <slot name="other" :userName="user">{{ user.test }}</slot> -->
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
      user: {
        test: "jack"
      }
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
h3 {
  height: 60px;
  line-height: 60px;
  text-align: center;
}
</style>
