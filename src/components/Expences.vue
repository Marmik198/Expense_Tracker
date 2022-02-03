<template>
  <div>
    <div class="expences">
      <div class="balance">
        <span>Balance</span>
        <p>&#8377;{{ allExpences.balance }}</p>
      </div>
      <div class="income">
        <span>Income</span>
        <p>&#8377;{{ allExpences.income }}</p>
      </div>
      <div class="expence">
        <span>Expence</span>
        <p>&#8377;{{ allExpences.expence * -1 }}</p>
      </div>
    </div>

    <h3 class="hist">History</h3>

    <div
      class="history"
      v-for="history in allExpences.history"
      :key="history.title"
      :class="[history.number > 0 ? 'border-green' : 'border-red']"
    >
      <div class="history__title">{{ history.title }}</div>
      <div class="history__number">&#8377;{{ history.number }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Expences",
  props: ["allExpences"],
};
</script>

<style scoped>
.expences {
  width: 800px;
  margin: 70px auto;
  display: flex;
  justify-content: space-between;
}
.balance {
  background: #ffff;
  padding: 20px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
  width: 250px;
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  border-bottom: 4px solid orange;
  border-radius: 20px;
}
.balance span {
  position: absolute;
  top: 0;
  /* left: 0; */
  text-align: center;
  width: 250px;
  background: orange;
  border-radius: 20px 20px 0 0;
  color: #fff;
  font-size: 20px;
  padding: 5px;
}
.income {
  background: #ffff;
  padding: 20px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
  width: 250px;
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  border-bottom: 4px solid #42b983;
  border-radius: 20px;
}
.income span {
  position: absolute;
  top: 0;
  /* left: 0; */
  text-align: center;
  width: 250px;
  background: #42b983;
  border-radius: 20px 20px 0 0;
  color: #fff;
  font-size: 20px;
  padding: 5px;
}
.expence {
  background: #ffff;
  padding: 20px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
  width: 250px;
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  border-bottom: 4px solid #f44336;
  border-radius: 20px;
}
.expence span {
  position: absolute;
  top: 0;
  /* left: 0; */
  text-align: center;
  width: 250px;
  background: #f44336;
  border-radius: 20px 20px 0 0;
  color: #fff;
  font-size: 20px;
  padding: 5px;
}
p {
  margin-top: 10px;
  font-size: 30px;
}

.hist {
  font-size: 25px;
  text-align: center;
  border-bottom: 1px solid gray;
  width: 800px;
  margin: 0 auto 15px;
}
.history {
  width: 800px;
  margin: 15px auto;
  background: #fff;
  padding: 12px;
  display: flex;
  animation: animate 0.5s linear;
}
@keyframes animate {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
.history__title {
  width: 70%;
}
.history__number {
  width: 30%;
  text-align: right;
}
.border-green {
  border-left: 3px solid #42b983;
}
.border-red {
  border-left: 3px solid #f44336;
}
</style>
