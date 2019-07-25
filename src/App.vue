<template>
  <div id="app">
    <h1>PlatformWD Test App</h1>
    <QuantityInput @inputData="updateMessage" :parentData="minimax"/>
    <h3>Quantity of apples is {{ childData }} kg.</h3>
    <h5>*quantity must be more then {{ minimax.selectedmin }} kg</h5>
    <h5>*quantity must be less then {{ minimax.selectedmax + 1}} kg</h5>
  </div>
</template>

<script>
import QuantityInput from './components/QuantityInput.vue'
export default {
  name: 'app',
  components: {
    QuantityInput
  },
  data () {
    return {
      childData: '',
      minimax: {
      selectedmin: 1,
      selectedmax: 99
      }
    }
  },
  methods: {
    updateMessage(variable) {
      this.childData = variable;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
