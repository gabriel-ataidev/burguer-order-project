<template>
  <div>
    <p>message component</p>
    <div class="form-container">
      <form id="burger-form">
        <div class="input-container">
          <label for="name">Nome do cliente</label>
          <input
            type="text"
            id="name"
            name="name"
            v-model="name"
            placeholder="Digite seu nome"
            autocomplete="off"
          />
        </div>
        <div class="input-container">
          <label for="bread">Escolha o pão</label>
          <select name="bread" id="bread" v-model="bread">
            <option value="">Selecione o seu pão</option>
            <option value="integral">Integral</option>
          </select>
        </div>
        <div class="input-container">
          <label for="meat">Selecione a carne do seu burger</label>
          <select name="meat" id="meat" v-model="meat">
            <option value="">Selecione a carne</option>
            <option value="maminha">Maminha</option>
          </select>
        </div>
        <div class="input-container optional-container">
          <label id="optional-title" for="optional"
            >Selecione a carne do seu burger</label
          >
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="optional"
              id="optional"
              v-model="optional"
              value="salame"
            />
            <span>Salame</span>
          </div>
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="optional"
              id="optional"
              v-model="optional"
              value="salame"
            />
            <span>Salame</span>
          </div>
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="optional"
              id="optional"
              v-model="optional"
              value="salame"
            />
            <span>Salame</span>
          </div>
        </div>
        <div class="input-container">
          <input type="submit" class="submit-btn" value="Criar meu burger" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "BurgerForm",
};
</script>

<style scoped lang="less">
.form-container{
    display: flex;
    justify-content: center;
    #burger-form {
      max-width: 350px;
      margin: 0 auto;
      .input-container {
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
        label {
          font-weight: bold;
          margin-bottom: 15px;
          color: #222;
          padding: 5px 10px;
          border-left: 4px solid #fcba03;
        }
        input,
        select {
          padding: 5px 10px;
          width: 100%;
        }
      }
      .optional-container {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        #optional-title{
            width: 100%;
        }
        .checkbox-container {
          display: flex;
          align-items: flex-start;
          width: 50%;
          margin-bottom: 10px;
          span, input{
              width: auto;
          }
          span{
              margin-left: 6px;
          }
        }
      }
      .submit-btn{
          background: #222;
          color: #fcba03;
          border: 2px solid #222;
          border-radius: 10px;
          padding: 10px;
          font-size: 20px;
          margin: 0 auto;
          cursor: pointer;
          transition: all .4s ease-in-out;
          &:hover{
              background: transparent;
              color: #222;
          }
      }
    }
}
</style>
