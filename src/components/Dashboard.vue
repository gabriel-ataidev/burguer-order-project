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
      <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
        <div class="order-number"> {{burger.id}} </div>
        <div> {{burger.name}} </div>
        <div> {{burger.bread}} </div>
        <div> {{burger.meat}} </div>
        <div>
          <ul>
            <li v-for="(optional, index) in burger.optionals" :key="index"> {{optional}} </li>
          </ul>
        </div>
        <div>
          <select name="status" class="status" @change="updateBurger($event, burger.id)">
            <option v-for="s in status" :key="s.id" :value="s.tipo" :selected="burger.status == s.tipo"> {{s.tipo}} </option>
          </select>
          <button class="delete-btn" @click="deleteBurger(burger.id)">Cancelar</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Dashboard",
  data() {
    return {
      burgers: null,
      burger_id: null,
      status: [],
    };
  },
  methods: {
    async getOrders() {
      const req = await fetch("http://localhost:3000/burgers");
      const data = await req.json();
      this.burgers = data;

      //getting data
      this.getStatus();
    },
    async getStatus() {
      const req = await fetch("http://localhost:3000/status");
      const data = await req.json();
      this.status = data;
    },
    async deleteBurger(id) {
      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "DELETE"
      });
      const res = await req.json();
      this.getOrders();
    },
    async updateBurger(event, id) {
      const option = event.target.value;
      const dataJson = JSON.stringify({ status: option});
      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "PATCH",
        headers: {"Content-Type": "application/json"},
        body: dataJson
      });
      const res = await req.json();
      console.log(res);

    }
  },
  mounted() {
    this.getOrders();
  },
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
    ul {
      list-style: none;
    }
    select {
      padding: 12px 6px;
      margin-right: 12px;
      border-radius: 10px;
    }
    .delete-btn {
      background: #222;
      color: #fcba03;
      border: 2px solid #222;
      border-radius: 10px;
      padding: 10px;
      font-size: 16px;
      margin: 5px auto 0;
      cursor: pointer;
      transition: all 0.4s ease-in-out;
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
