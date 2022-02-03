<template>
  <v-app class="white">
    <v-main>
      <Navbar @model-show="modelToggle" />
      <Model
        @model-toggle="modelToggle"
        :status="modelStatus"
        @store-expence="storeExpence"
      />
      <Expences :allExpences="expences" />
    </v-main>
    <v-footer app class="justify-center pt-4 pb-4">
      <h3>&copy; Copyright - <a href="#">Marmik Shah</a></h3>
      <h3><a href="#">Project Link</a></h3>
    </v-footer>
  </v-app>
</template>

<script>
import Navbar from "./components/Navbar";
import Model from "./components/Model.vue";
import Expences from "./components/Expences.vue";

export default {
  name: "App",
  components: {
    Navbar,
    Model,
    Expences,
  },

  data() {
    return {
      modelStatus: false,
      expences: {
        balance: 0,
        income: 0,
        expence: 0,
        history: [],
      },
    };
  },

  methods: {
    modelToggle() {
      this.modelStatus = !this.modelStatus;
    },

    storeExpence(payload) {
      const number = parseInt(payload.number);
      if (number > 1) {
        this.expences = {
          ...this.expences,
          income: this.expences.income + number,
          balance: this.expences.balance + number,
          history: [{ title: payload.title, number }, ...this.expences.history],
        };
      } else if (number < 1) {
        this.expences = {
          ...this.expences,
          expence: this.expences.expence + number,
          balance: this.expences.balance + number,
          history: [{ title: payload.title, number }, ...this.expences.history],
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
