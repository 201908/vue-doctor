<template>
  <div class="home">
    <header>陆川县人民医院</header>
    <ul class="ul-link">
      <li class="link" v-for="(item,index) in links" :key="index">
        <router-link to="/appointment">
          <img :src="item.src" alt />
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: "home",
  data() {
    return {
      links: [
        {
          src: "/img/index-btn1.png"
        },
        {
          src: "/img/index-btn1.png"
        },
        {
          src: "/img/index-btn1.png"
        },
        {
          src: "/img/index-btn1.png"
        },
        {
          src: "/img/index-btn1.png"
        },
        {
          src: "/img/index-btn1.png"
        },
        {
          src: "/img/index-btn1.png"
        },
        {
          src: "/img/index-btn1.png"
        }
      ]
    };
  }
};
</script>
<style scoped lang="less">
header {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 150px;
  font-size: 40px;
  color: #fff;
}
.home {
  height: 1080px;
  background: url(../assets/bg-best.jpg) no-repeat center 0;
}
@media only screen and(max-width:1024px) {
  .home {
    height: 768px;
    background: url(../assets/bg-better.jpg) no-repeat center 0;
  }
}
.header {
  height: 150px;
}
.ul-link {
  display: flex;
  flex-wrap: wrap;
  width: 1024px;
  margin: 0 auto;
  .link {
    flex: 1 1 25%;
    margin-top: 40px;
    text-align: center;
  }
}
</style>
