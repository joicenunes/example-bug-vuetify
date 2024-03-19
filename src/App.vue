<template>
  <div id="app">
    <div class="example">
      <v-text-field
        v-model="valor"
        dense
        outlined
        placeholder="0,00"
        prefix="R$"
        @keypress="tratarValorPressionado"
        @input="tratarValor"
      ></v-text-field>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: "App",
  data: () => ({
    valor: "",
  }),
  methods: {
    tratarValorPressionado: function (event) {
      let char = String.fromCharCode(event.keyCode);
      if (/\d/.test(char)) return true;
      else event.preventDefault();
    },
    tratarValor: async function () {
      this.valor = this.valor.replace(/\D/g, "");
      if (this.valor.length > 0) {
        const valorEmDecimais = Number(this.valor) / 100;
        this.valor = valorEmDecimais.toFixed(2).replace(".", ",");
      }
    },
  },
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
