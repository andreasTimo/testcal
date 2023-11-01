<!-- <script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script> -->
<template>
  <div id="app">
    <h1>Vue.js Calculator</h1>
    <Cal @clear="clear" @update-result="updateResult" @evaluate="evaluate" />
    <div class="result">
      <p>Result: {{ result }}</p>
    </div>
  </div>
</template>

<script>
import Cal from './components/cal.vue';

export default {
  components: {
    Cal,
  },
  data() {
    return {
      result: '',
    };
  },
  methods: {
    clear() {
      this.result = '';
    },
    updateResult(expression) {
      try {
        this.result = eval(expression);
      } catch (error) {
        this.result = 'Error';
      }
    },
    evaluate(expression) {
      try {
        this.result = eval(expression);
      } catch (error) {
        this.result = 'Error';
      }
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.result {
  margin-top: 20px;
}
</style>
