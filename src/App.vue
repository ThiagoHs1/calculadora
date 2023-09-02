<script setup>
import { ref, watch } from "vue";

const numero1 = ref(0);
const numero2 = ref(0);
const operacao = ref("+");
const resultado = ref(0);

watch([numero1, numero2, operacao], () => {
  calcular();
});

const calcular = () => {
  const num1 = parseFloat(numero1.value);
  const num2 = parseFloat(numero2.value);

  switch (operacao.value) {
    case "+":
      resultado.value = num1 + num2;
      break;
    case "-":
      resultado.value = num1 - num2;
      break;
    case "*":
      resultado.value = num1 * num2;
      break;
    case "/":
      resultado.value = num1 / num2;
      break;
    default:
      resultado.value = 0;
  }
};
</script>

<template class="">
<div class="home">  
  <div class="container">
    <header class=" p-5 mb-4 rounded-3">
      <h1>Calculadora Aritmética</h1>
    </header>

    <div class="calculadora">
      <div class="row">
        <div class="col">
          <input
            type="text"
            placeholder="Digite o primeiro número"
            v-model="numero1"
          />
        </div>

        <div class="col-md-3">
          <select v-model="operacao" @change="calcular()">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
          </select>
        </div>

        <div class="col-md-4">
          <input
            type="text"
            placeholder="Digite o segundo número"
            v-model="numero2"
          />
        </div>
        <div class="row">
          <div class="col resultado">
            <p>O resultado é: <b>{{ resultado }}</b></p>
          </div>
        </div>
      </div>
    </div>
  </div></div>
</template>

<style scoped>

.home {
  background-color: #0984e3;
  padding: 0px;
  height: 100vh;
  width: 100%;

}

header {
  text-align: center;
  background-color: aliceblue;
}

.calculadora {
  width: 100%;
  max-width: 60%;
  margin: 0 auto;
  text-align: center;
}

b {
  font-size: 30px;
  color: aliceblue;
  font-weight: bold;
  
}

.resultado {
  margin-top: 30px;
  font-size: 25px;
}

input {
  width: 100%;
  height: 30px;
  font-size: 25px;
  padding: 15px;
  outline: none;
  border-radius: 10px;
}

select {
  width: 50%;
  height: 30px;
  text-align: center;
  border-radius: 10px;
}
</style>
