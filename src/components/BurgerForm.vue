<template>
  <div>
    <Modal :msg="msg" v-show="msg"/>
    <div class="form-container">
      <form id="burger-form" @submit="createBurger">
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
            <option v-for="bread in breads" :key="bread.id" :value="bread.tipo">
              {{ bread.tipo }}
            </option>
          </select>
        </div>
        <div class="input-container">
          <label for="meat">Selecione a carne do seu burger</label>
          <select name="meat" id="meat" v-model="meat">
            <option v-for="meat in meats" :key="meat.id" :value="meat.tipo">
              {{ meat.tipo }}
            </option>
          </select>
        </div>
        <div class="input-container optional-container">
          <label id="optional-title" for="optional"
            >Selecione os opcionais</label
          >
          <div
            class="checkbox-container"
            v-for="optional in optionalsData"
            :key="optional.id"
          >
            <input
              type="checkbox"
              name="optionals"
              id="optional"
              v-model="optionals"
              :value="optional.tipo"
            />
            <span> {{ optional.tipo }} </span>
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
import Modal from './Modal.vue';

export default {
  name: "BurgerForm",
  components: {
      Modal,
  },
  data() {
      return {
          name: null,
          bread: null,
          meat: null,
          optionalsData: null,
          breads: null,
          meats: null,
          optionals: [],
          msg: null,
      }
  },
  methods: {
      async getIngredients() {
          const req = await fetch("http://localhost:3000/ingredientes");
          const data = await req.json();

            this.breads = data.paes;
            this.meats = data.carnes;
            this.optionalsData = data.opcionais;
      },
      async createBurger(e) {
          e.preventDefault();
          const data = {
              name: this.name,
              meat: this.meat,
              bread: this.bread,
              optionals: Array.from(this.optionals),
              status: "Solicitado"
          }
          const dataJson = JSON.stringify(data);

          const req = await fetch("http://localhost:3000/burgers", {
              method: "POST",
              headers: {"content-type": "application/json"},
              body: dataJson
          });
          const res = await req.json();

        //send msg
        this.msg = `Pedido nº${res.id} realizado com sucesso`;

        //clear msg
        setTimeout(() => this.msg = "", 2000);

        //clear inputs
          this.carne = '';
          this.bread = '';
          this.name = '';
          this.optionals = [];
      }
  },
  mounted() {
      this.getIngredients();
  }
};
</script>

<style scoped lang="less">
.form-container {
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
      #optional-title {
        width: 100%;
      }
      .checkbox-container {
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 10px;
        span,
        input {
          width: auto;
        }
        span {
          margin-left: 6px;
        }
      }
    }
    .submit-btn {
      background: #222;
      color: #fcba03;
      border: 2px solid #222;
      border-radius: 10px;
      padding: 10px;
      font-size: 20px;
      margin: 0 auto;
      cursor: pointer;
      transition: all 0.4s ease-in-out;
      &:hover {
        background: transparent;
        color: #222;
      }
    }
  }
}
</style>
