<template>
  <div class="modal">
     <p> {{msg}} </p>
  </div>
</template>

<script>
export default {
    name: "Modal",
    props: {
        msg: String,
    }

}
</script>

<style scoped lang="less">
.modal{
    color: #004085;
    background: #cce5ff;
    border: 2px solid #b8daff;
    border-radius: 5px;
    max-width: 350px;
    margin: 30px auto;
    padding: 10px 20px;
}
</style>