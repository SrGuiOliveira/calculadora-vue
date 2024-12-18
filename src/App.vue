<script setup>
import { reactive } from 'vue';

const estado = reactive({
  num1: 0,
  num2: 0,
  operacao: '',
  resultado: 0,
});

const somar = () => estado.num1 + estado.num2;
const subtrair = () => estado.num1 - estado.num2;
const multiplicar = () => estado.num1 * estado.num2;
const dividir = () => estado.num1 / estado.num2;

const fazerOperacao = () => {
  switch (estado.operacao) {
    case '+':
      estado.resultado = somar();
      break;
    case '-':
      estado.resultado = subtrair();
      break;
    case 'x':
      estado.resultado = multiplicar();
      break;
    case '/':
      estado.resultado = dividir();
      break;
    default:
      estado.resultado = 0;
  }
};
</script>



<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-secondary rounded-3">
      <h1 class="text-center text-uppercase fw-bolder fst-italic">Calculadora aritmética</h1>
      <h2 class="text-center">Selecione dois números abaixo e escolha a operação aritmética.</h2>
    </header>
    <form class="bg-light p-5">
      <div class="row align-items-center">
        <div class="col-md-2">
          <input @input="evento => { estado.num1 = Number(evento.target.value); fazerOperacao(); }" type="number" class="form-control" placeholder="000000000000">
        </div>
        <div class="col-md-2">
          <select @change="evento => { estado.operacao = evento.target.value; fazerOperacao(); }" class="p-1 w-100 text-center">
            <option value="Selecione">Selecione</option>
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="x">x</option>
            <option value="/">/</option>
          </select>
        </div>
        <div class="col-md-2">
          <input @input="evento => { estado.num2 = Number(evento.target.value); fazerOperacao(); }" type="number" class="form-control" placeholder="000000000000">
        </div>
        <div class="col-md-2 ps-0 pe-0">
          <p class="resultado mb-0 fs-5 fw-bolder text-uppercase text-center">Resultado: </p>
        </div>
        <div class="col-md-3">
          <span class="p-2 fs-4 fw-bold">{{ estado.resultado }}</span>
        </div>
      </div>
    </form>
  </div>
</template>



<style scoped>

</style>
