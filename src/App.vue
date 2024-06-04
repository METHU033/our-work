<template>
  <div id="app" class="container">
    <div class="holder">
      <h1>BMI Calculator</h1>
      <div>
        <label for="weight">Weight (kg):</label>
        <input type="number" id="weight" v-model="weight">
      </div><br>
      <div>
        <label for="height">Height (m):</label>
        <input type="number" id="height" v-model="height">
      </div><br><br>
      <button @click="calculate" class="btn">Calculate BMI</button>
      <p>Your BMI is: {{ bmi }}</p>
      <p>Weight Category: {{ weightCategory }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      weight: 0,
      height: 0,
      bmi: 0,
      weightCategory: "",
    };
  },
  computed: {
    formValid() {
      return +this.height > 0 && +this.weight > 0;
    },
  },
  methods: {
    calculate() {
      if (!this.formValid) {
        return;
      }
      this.bmi = this.weight / (this.height ** 2);
      this.weightCategory = this.getWeightGroup(this.bmi);
    },
    getWeightGroup(bmi) {
      if (bmi < 18.5) {
        return "Underweight";
      } else if (bmi < 24.9) {
        return "Normal weight";
      } else if (bmi < 29.9) {
        return "Overweight";
      } else {
        return "Obesity";
      }
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  border: 5px solid black;
  border-radius: 10px;
  margin-left: 60em;
  background-color: rgb(151, 41, 41);
  margin-top: 9em;
}
.holder{
  margin-left: -4em;
}
label{
  font-family: sans-serif;
  font-size: 20px;
  font-weight: 900;
}
input{
  width: 300px;
  height: 3em;
}
.btn{
  width: 300px;
  height: 3em;
  color: brown;
  background-color: gray;
  margin-left: 6.5em;
  font-family: sans-serif;
  font-size: 20px;
  font-weight: 900;
  border-radius: 10px;
  border: none;
}
p{
  font-family: sans-serif;
  font-size: 20px;
  font-weight: 900;
}
</style>
