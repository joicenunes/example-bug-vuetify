<template>
  <div class="currency-field">
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
</template>

<script>
export default {
  name: "CurrencyField",
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
