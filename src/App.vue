<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Calculadora from './components/Calculadora.vue';

const calculadora = reactive({
  numero1: null,
  numero2: null,
  operador: 'mais',
  resultado: 'Aguardando parâmetros...'
})

function operadoresValidos() {
  const operador1 = parseInt(calculadora.numero1);
  const operador2 = parseInt(calculadora.numero2);
  if ((isNaN(operador1)) || (isNaN(operador2))) {
    calculadora.resultado = 'Aguardando parâmetros...';
    return false;
  } else {
    return true;
  }
}

function calculaResultado() {
  const operador1 = parseInt(calculadora.numero1);
  const operador2 = parseInt(calculadora.numero2);

  switch (calculadora.operador) {
    case 'mais': calculadora.resultado = operador1 + operador2;
      operadoresValidos();
      return calculadora.resultado
    case 'menos': calculadora.resultado = operador1 - operador2;
      operadoresValidos();
      return calculadora.resultado
    case 'vezes': calculadora.resultado = operador1 * operador2;
      operadoresValidos();
      return calculadora.resultado
    case 'divisao': calculadora.resultado = operador1 / operador2;
      operadoresValidos();
      return calculadora.resultado
    default:
      return alert('erro ao calcular');
  }
}

function atualizaOperador() {  
  calculadora.operador = document.getElementById('operador').value;
  calculaResultado();
}

function atualizaNumero1() {
  const numero = document.getElementById('numero1').value;
  calculadora.numero1 = numero
  if (!isNaN(numero)) {
    calculaResultado();
  } else {
    calculadora.resultado = 'Aguardando parâmetros...';
  }
}

function atualizaNumero2() {
 const numero = document.getElementById('numero2').value;
  calculadora.numero2 = numero
  if (!isNaN(numero)) {
    calculadora.numero2 = numero
    calculaResultado();
  } else {
    calculadora.resultado = 'Aguardando parâmetros...';
  }
}

</script>

<template>
  <div class="container">
    <Cabecalho />
    <Calculadora :atualiza-numero1="atualizaNumero1" :atualiza-numero2="atualizaNumero2" :atualiza-operador="atualizaOperador" :operadores-validos="operadoresValidos()"  :resultado="calculadora.resultado"/>
    
  </div>
</template>

<style scoped>

</style>
