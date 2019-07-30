<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>-->
    <router-view />
  </div>
</template>

<style lang="less">
* {
  margin: 0;
  padding: 0;
}
ul {
  list-style-type: none;
}
.red {
  color: red;
}
.ul-global {
  display: flex;
  flex-wrap: wrap;
  padding: 0 100px;
  height: 450px;
  overflow: hidden;
  li {
    flex: 0 1 23%;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 90px;
    margin: 10px 20px;
    padding: 20px;
    border-radius: 30px;
    font-size: 32px;
    text-align: center;
    color: #fff;
    background: #18abef;
    // box-sizing: border-box; ie不支持
    &.currentColor {
      background: palegreen;
    }
  }
}
// #app {
//   font-family: "Avenir", Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
// }
// #nav {
//   padding: 30px;
//   a {
//     font-weight: bold;
//     color: #2c3e50;
//     &.router-link-exact-active {
//       color: #42b983;
//     }
//   }
// }
</style>
