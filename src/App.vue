<template>
  <nav class="menu-nav">
    <router-link to="/">菜单UI</router-link> |
    <router-link to="/about">其他..</router-link>
  </nav>
  <router-view />
</template>

<script>
export default {
  name: "App",
};
</script>

<style lang='less'>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  height: 100%;
  .menu-nav {
    height: 30px;
    line-height: 30px;
    border-top: 1px solid #ccc;
    border-bottom: 1px solid #ccc;
  }
}
* {
  margin: 0;
  padding: 0;
}
body {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 14px;
  color: #000;
}
li,
ul,
p,
div,
body,
html,
table {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html,
body {
  height: 100%;
  overflow: hidden;
  box-sizing: border-box;
}
li {
  list-style: none;
}
a,
h1,
h2,
h3,
h4,
h5,
h6,
th {
  text-decoration: none;
  color: #000;
}
button {
  border: 0;
}
input {
  border: 1px solid skyblue;
  outline: none;
  height: 20px;
  padding: 2px 4px;
}
textarea {
  border: 1px solid skyblue;
  outline: none;
  padding: 2px 4px;
  resize: none;
}
.set-btn {
  display: inline-block;
  height: 30px;
  line-height: 30px;
  text-align: center;
  padding: 0 6px;
  border: 1px solid skyblue;
  border-radius: 3px;
  cursor: pointer;
  background-color: #fff;
  &:hover {
    background-color: skyblue;
    color: #fff;
  }
}
.set-active {
  border: 0;
  background-color: skyblue;
  color: #fff;
}
</style>
