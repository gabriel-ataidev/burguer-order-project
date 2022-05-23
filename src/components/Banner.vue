<template>
  <div id="main-banner">
      <h1>MAKE <br> YOUR <br> BURGER</h1>
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
    background-position: center;
    background-size: cover;
    height: 90vh;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    h1{
        color: #fff;
        align-items: center;
        font-size: 110px;
        padding-left: 90px;
    }
}
</style>