<template>
  <div id="app">
    <div class="example">
      <currency-field></currency-field>
    </div>
  </div>
</template>

<script lang="ts">
import CurrencyField from "./components/CurrencyField.vue";
export default {
  name: "App",
  components: { CurrencyField },
};
</script>

<style>
.example {
  max-width: 200px;
  margin: 100px auto;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
