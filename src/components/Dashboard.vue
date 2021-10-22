<template>
  <div class="burger-table">
    <div id="burger-table-heading">
      <div class="order-id">#</div>
      <div>Cliente:</div>
      <div>Pão:</div>
      <div>Carne</div>
      <div>Opcionais:</div>
      <div>Ações:</div>
    </div>
    <div id="burger-table-rows">
      <div class="burger-table-row">
        <div class="order-number">1</div>
        <div>João</div>
        <div>Pão de trigo</div>
        <div>Maminha</div>
        <div>
          <ul>
            <li>Salame</li>
            <li>Tomate</li>
          </ul>
        </div>
        <div>
          <select name="status" class="status">
            <option value="">Selecione</option>
          </select>
          <button class="delete-btn">Cancelar</button>
        </div>
      </div>
    </div>
    <div id="burger-table-rows">
      <div class="burger-table-row">
        <div class="order-number">1</div>
        <div>João</div>
        <div>Pão de trigo</div>
        <div>Maminha</div>
        <div>
          <ul>
            <li>Salame</li>
            <li>Tomate</li>
          </ul>
        </div>
        <div>
          <select name="status" class="status">
            <option value="">Selecione</option>
          </select>
          <button class="delete-btn">Cancelar</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Dashboard",
};
</script>

<style scoped lang="less">
.burger-table {
  max-width: 1200px;
  margin: 0 auto;
  min-height: 53vh;
  #burger-table-heading,
  #burger-table-rows,
  .burger-table-row {
    display: flex;
    flex-wrap: wrap;
  }
  #burger-table-heading {
    padding: 12px;
    border-bottom: 3px solid #333;
  }
  .burger-table-row {
    align-items: center;
    width: 100%;
    padding: 12px;
    border-bottom: 1px solid #ccc;
    ul{
        list-style: none;
    }
    select{
        padding: 12px 6px;
        margin-right: 12px;
        border-radius: 10px;
    }
    .delete-btn{
    background: #222;
      color: #fcba03;
      border: 2px solid #222;
      border-radius: 10px;
      padding: 10px;
      font-size: 16px;
      margin: 5px auto 0;
      cursor: pointer;
      transition: all .4s ease-in-out;
      &:hover {
        background: transparent;
        color: #222;
      }
    }
  }
  #burger-table-heading div,
  .burger-table-row div {
    width: 19%;
  }
  #burger-table-heading .order-id,
  .burger-table-row .order-number {
    width: 5%;
  }
}
</style>
