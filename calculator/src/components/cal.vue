<template>
    <div class="calculator">
      <input v-model="expression" placeholder="Enter expression" @input="updateResult" />
      <button @click="clear">C</button>
      <button @click="evaluate">=</button>
      <div class="buttons">
        <button v-for="digit in digits" :key="digit" @click="appendDigit(digit)">{{ digit }}</button>
        <button v-for="operator in operators" :key="operator" @click="appendOperator(operator)">{{ operator }}</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        expression: '',
      };
    },
    computed: {
      digits() {
        return ['1', '2', '3', '4', '5', '6', '7', '8', '9', '0'];
      },
      operators() {
        return ['+', '-', '*', '/'];
      }
    },
    methods: {
      appendDigit(digit) {
        this.expression += digit;
      },
      appendOperator(operator) {
        this.expression += operator;
      },
      clear() {
        this.expression = '';
        this.$emit('clear');
      },
      updateResult() {
        this.$emit('update-result', this.expression);
      },
      evaluate() {
        this.$emit('evaluate', this.expression);
      }
    }
  };
  </script>
  
  <style scoped>
  .calculator {
    width: 300px;
    margin: 0 auto;
  }
  
  input {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
  }
  
  button {
    width: 70px;
    height: 70px;
    font-size: 18px;
    margin: 5px;
    cursor: pointer;
  }
  
  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
  }
  </style>
  