<script setup>
import { reactive } from 'vue';

const estado = reactive({
  numeroA: 0,
  numeroB: 0,
  resultado: 0,

  operacao: '',
})

const sum = () => {
  let numA = estado.numeroA;
  let numB = estado.numeroB;
  let resultado = estado.resultado;

  resultado = parseFloat(numA) + parseFloat(numB);

  return estado.resultado = resultado
}

const min = () => {
  let numA = estado.numeroA;
  let numB = estado.numeroB;
  let resultado = estado.resultado;

  resultado = numA - numB;

  return estado.resultado = resultado
}

const mult = () => {
  let numA = estado.numeroA;
  let numB = estado.numeroB;
  let resultado = estado.resultado;

  resultado = numA * numB;

  return estado.resultado = resultado
}

const div = () => {
  let numA = estado.numeroA;
  let numB = estado.numeroB;
  let resultado = estado.resultado;

  resultado = numA / numB;

  return estado.resultado = resultado
}

function calcularOp() {
  const { operacao } = estado;

  switch (operacao) {
    case '1':
      return sum();
    case '2':
      return min();
    case '3':
      return mult();
    case '4':
      return div();
    default:
      alert('Selecione a operação desejada!')
  }
}
</script>

<template>
  <div class="container text-center">
    <header class="d-flex align-items-center justify-content-between m-3">
      <h1>Calculadora</h1>
    </header>
    <div class="row">
      <div class="col mt-5 p-5">
        <form class="justify-content-between align-items-center p-5" @change="calcularOp()" @submit.prevent="calcularOp">
          <input @change="evento => estado.numeroA = evento.target.value" class="form-control m-2" type="number"
            placeholder="0" required>
            <button class="col btn btn-outline-dark btn-lg m-3" value="1" @click="evento => estado.operacao = evento.target.value">+</button>
            <button class="col btn btn-outline-dark btn-lg m-3" value="2" @click="evento => estado.operacao = evento.target.value">-</button>
            <button class="col btn btn-outline-dark btn-lg m-3" value="3" @click="evento => estado.operacao = evento.target.value">x</button>
            <button class="col btn btn-outline-dark btn-lg m-3" value="4" @click="evento => estado.operacao = evento.target.value">/</button>
          <input @change="evento => estado.numeroB = evento.target.value" class="form-control m-2" type="number"
            placeholder="0" required>
          <span>=</span>
          <input class="form-control m-2" type="number" disabled :value="estado.resultado">
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  
}
.dark{
  background-color: rgb(20, 19, 19);
  color: rgb(215, 202, 229)
}

</style>
