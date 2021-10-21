<template>
  <div id="main-banner">
      <h1>MAKE YOUR BURGUER</h1>
  </div>
</template>

<script>
export default {
    name: "Banner",

}
</script>

<style scoped lang="less">
#main-banner{
    background-image: url('/img/burger.jpg');
    background-position: 0 -250px;
    background-size: cover;
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    h1{
        color: #fff;
        align-items: center;
        font-size: 50px;
        padding-left: 60px;
    }
}
</style>