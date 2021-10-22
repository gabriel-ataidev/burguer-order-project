<template>
  <footer>
    <img src="/img/instagram-icon.png" />
    <p>MAKE YOUR BURGUER &copy; 2021</p>
    <img src="/img/whatsapp-icon.png" />
  </footer>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style lang="less">
footer{
  display: flex;
  align-items: center;
  justify-content: center;
  height: 10vh;
  background: #222;
  border-top: 4px solid #111;
  color: #fcba03;
  width: 100%;
  p{
    max-width: fit-content;
    margin: 0 50px;
    font-size: 18px;
  }
  img{
    height: 30px;
    width: auto;
    cursor: pointer;
    transition: all .4s ease-in-out;
    &:hover{
      opacity: 0.7;
    }
  }
}
</style>
