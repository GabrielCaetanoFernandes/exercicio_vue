<template>
    <div class="row">
        <div class="col mt-5 p-5">
            <form class="justify-content-between align-items-center p-5" @submit.prevent="calcularOp">
                <input v-model="estado.numeroA" class="form-control m-2" type="number" placeholder="0" required>
                <button class="col btn btn-outline-dark btn-lg m-3" value="1" @click="setOperation('+')">+</button>
                <button class="col btn btn-outline-dark btn-lg m-3" value="2" @click="setOperation('-')">-</button>
                <button class="col btn btn-outline-dark btn-lg m-3" value="3" @click="setOperation('*')">*</button>
                <button class="col btn btn-outline-dark btn-lg m-3" value="4" @click="setOperation('/')">/</button>
                <input v-model="estado.numeroB" class="form-control m-2" type="number" placeholder="0" required>
                <span>=</span>
                <input class="form-control m-2" type="number" disabled :value="estado.resultado">
            </form>
        </div>
    </div>
</template>
  
<script setup>
import { reactive } from 'vue';

const estado = reactive({
    numeroA: 0,
    numeroB: 0,
    resultado: 0,
    operacao: '',
});

const setOperation = (operation) => {
    estado.operacao = operation;
};

const calcularOp = () => {
    switch (estado.operacao) {
        case '+':
            estado.resultado = parseFloat(estado.numeroA) + parseFloat(estado.numeroB);
            break;
        case '-':
            estado.resultado = parseFloat(estado.numeroA) - parseFloat(estado.numeroB);
            break;
        case '*':
            estado.resultado = parseFloat(estado.numeroA) * parseFloat(estado.numeroB);
            break;
        case '/':
            estado.resultado = parseFloat(estado.numeroA) / parseFloat(estado.numeroB);
            break;
        default:
            alert('Selecione a operação desejada!');
    }
};
</script>
  