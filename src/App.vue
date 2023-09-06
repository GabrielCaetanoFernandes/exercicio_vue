<script setup>
import { reactive } from 'vue';

const estado = reactive({
  numeroA: 0,
  numeroB: 0,
  resultado: 0,

  operacao: '',
})

const teste = () => {
  console.log(estado.numeroA, estado.numeroB, estado.operacao)
}

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
  <div class="container">
    <div class="row">
      <div class="col d-flex mt-5">
        <form class="d-flex" @submit.prevent="calcularOp">
          <input @change="evento => estado.numeroA = evento.target.value" class="form-control m-2" type="number"
            placeholder="0" required>
          <select class="form-control m-2" @change="evento => estado.operacao = evento.target.value">
            <option value="">Operação</option>
            <option value="1">+</option>
            <option value="2">-</option>
            <option value="3">x</option>
            <option value="4">/</option>
          </select>
          <input @change="evento => estado.numeroB = evento.target.value" class="form-control m-2" type="number"
            placeholder="0" required>
          <button class="btn btn-outline-primary m-2" type="submit">=</button>
          <input class="form-control m-2" type="number" disabled :value="estado.resultado">
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
