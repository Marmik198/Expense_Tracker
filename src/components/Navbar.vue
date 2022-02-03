<template>
  <nav>
    <v-app-bar flat app>
      <h2 class="font-weight-light">Expence</h2>
      <h2>Tracker</h2>
      <v-spacer></v-spacer>
      <v-btn @click="openModel" depressed class="blue white--text">
        <span>Add Expence</span>
        <i class="fas fa-plus ml-2" right></i>
      </v-btn>
    </v-app-bar>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
  methods: {
    openModel() {
      this.$emit("model-show");
    },
  },
};
</script>

<style scoped></style>
