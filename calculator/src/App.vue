<script setup>
import { reactive } from 'vue';


const calculator = reactive({
  result: 0,
  num1: 0,
  num2: 0,
  operation: 'sum',
});

function calculator1(evt) {
  
  calculator.num1 = parseInt(evt);

  aritimetic(calculator.operation);
}


function calculator2(evt) {

  calculator.num2 = parseInt(evt);

  aritimetic(calculator.operation);

}

function aritimetic(evt) {
  calculator.operation = evt;

  if (calculator.operation == 'sum') {
    sum(calculator.num1, calculator.num2);
  } else if (calculator.operation == 'substract') {
    substract(calculator.num1, calculator.num2);
  } else if (calculator.operation == 'multiply') {
    multiply(calculator.num1, calculator.num2);
  } else if (calculator.operation == 'divide') {
    divide(calculator.num1, calculator.num2);
  }

}
function sum(num1, num2) {
  calculator.result = num1 + num2;
}

function substract(num1, num2) {
  calculator.result = num1 - num2;
}

function multiply(num1, num2) {
  calculator.result = num1 * num2;
}

function divide(num1, num2) {
  calculator.result = num1 / num2;
}
</script>

<template>
  <div id="calculator">
    <h1>Calculadora</h1>
    <input type="number" id="number1" name="number1" @keyup="calculator1($event.target.value)">

    <select @change="aritimetic($event.target.value)">
      <option selected value="sum">+</option>
      <option value="substract">-</option>
      <option value="multiply">*</option>
      <option value="divide">/</option>
    </select>

    <input type="number" id="number2" name="number2" @keyup="calculator2($event.target.value)">

    <h3>= {{ calculator.result }}</h3>
   
  </div>
</template>

<style scoped></style>
