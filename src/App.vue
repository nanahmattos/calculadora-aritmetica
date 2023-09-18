<script setup>
import { reactive } from 'vue';

const estado = reactive ({
  num1: 0,
  num2: 0,
  operacao:'somar',
})

function calcula() {
  const {operacao} = estado

  switch(operacao){
    case 'subtrair':
    return (estado.num1) - (estado.num2)
    case 'dividir':
    return(estado.num1) *(estado.num2)
    case 'multiplicar':
    return(estado.num1) /(estado.num2)

    default: return parseInt(estado.num1) + parseInt(estado.num2) 
  }
}

</script>
<template>
  <div class="container  text-center">
    <header class="p-5">
      <h1>Calculadora Aritmética</h1>
      <p>Preencha os campos para calcular!</p>
    </header>
  <form>
    <div class="row">
          <div class="col-5">
            <input @keyup="AdicionaNum1 => estado.num1 = AdicionaNum1.target.value" type="number" required>
          </div>
          <div class="col-2">
            <select class="form-control" @change="evento => estado.operacao = evento.target.value">
                <option value="somar">+</option>
                <option value="subtrair">-</option>
                <option value="dividir">/</option>
                <option value="multiplicar">x</option>
            </select>
          </div>
          <div class="col-5">
            <input  @keyup="AdicionaNum2 => estado.num2 = AdicionaNum2.target.value" type="number" required>
          </div>
        </div>
      </form>
      <div class="row">
        <div class="col p-2 mt-4 bg-light fs-2 rounded-2">
          <p class="fs-5">Resultado:</p>
          <span>
            {{ calcula() }}
          </span>
        </div>
      </div>
  </div>
</template>

<style scoped>
</style>