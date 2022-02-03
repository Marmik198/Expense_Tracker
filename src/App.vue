<template>
  <v-app class="white">
    <v-main>
      <Navbar @model-show="modelToggle" />
      <Model
        @model-toggle="modelToggle"
        :status="modelStatus"
        @store-expense="storeExpense"
      />
      <Expenses :allExpenses="expenses" />
    </v-main>
    <v-footer app class="justify-center pt-4 pb-4">
      <h3>
        &copy; Copyright -
        <a href="https://github.com/Marmik198/">Marmik Shah -</a>
      </h3>
      <span> </span>
      <h3>
        <a href="https://github.com/Marmik198/Expense_Tracker"> Project Link</a>
      </h3>
    </v-footer>
  </v-app>
</template>

<script>
import Navbar from "./components/Navbar";
import Model from "./components/Model.vue";
import Expenses from "./components/Expenses.vue";

export default {
  name: "App",
  components: {
    Navbar,
    Model,
    Expenses,
  },

  data() {
    return {
      modelStatus: false,
      expenses: {
        balance: 0,
        income: 0,
        expense: 0,
        history: [],
      },
    };
  },

  methods: {
    modelToggle() {
      this.modelStatus = !this.modelStatus;
    },

    storeExpense(payload) {
      const number = parseInt(payload.number);
      if (number > 1) {
        this.expenses = {
          ...this.expenses,
          income: this.expenses.income + number,
          balance: this.expenses.balance + number,
          history: [{ title: payload.title, number }, ...this.expenses.history],
        };
      } else if (number < 1) {
        this.expenses = {
          ...this.expenses,
          expense: this.expenses.expense + number,
          balance: this.expenses.balance + number,
          history: [{ title: payload.title, number }, ...this.expenses.history],
        };
      }
      this.modelStatus = false;
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #fafafa;
  font-family: sans-serif;
}

.v-footer h3 a {
  color: black;
  text-decoration: none;
}

.v-footer h3 a:hover {
  text-decoration: none;
  color: #2196f3;
}
</style>
