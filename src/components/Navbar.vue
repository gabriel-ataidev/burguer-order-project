<template>
  <div id="nav">
    <router-link to="/" id="logo-url">
      <span id="title">MYB</span>
      <img id="logo" :src="logo" :alt="alt" />
    </router-link>
    <div class="links">
      <router-link to="/">Home</router-link>
      <router-link to="/pedidos">Pedidos</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  props: ["logo", "alt"],
};
</script>

<style scoped lang="less">
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
#nav {
  background: #222;
  border-bottom: 4px solid #111;
  padding: 10px 90px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-height: 15vh;
  a {
    color: #fcba03;
    font-size: 25px;
    text-decoration: none;
    margin: 0 12px;
    transition: all 0.5s ease-in-out;
    &:hover {
      color: #fff;
    }
  }
  #title{
    font-size: 45px;
    color: #fff;
  }
  #logo-url {
    margin: 5px 40px 0 0;
    #logo {
      height: 40px;
      width: auto;
    }
  }
  .links{
    display: flex;
    gap: 30px;
    align-items: center;
  }
}
</style>
