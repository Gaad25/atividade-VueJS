<template>
  <div id="app">
    <input v-model.number="numero1" type="number" placeholder="Número 1">
    <input v-model.number="numero2" type="number" placeholder="Número 2">
    <select v-model="operacao">
      <option value="soma">Soma</option>
      <option value="subtracao">Subtração</option>
      <option value="multiplicacao">Multiplicação</option>
      <option value="divisao">Divisão</option>
    </select>
    <h3>Resultado: {{ resultado }}</h3>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacao: 'soma',
      resultado: 0
    };
  },
  watch: {
    numero1: function (val) {
      this.calcular();
    },
    numero2: function (val) {
      this.calcular();
    },
    operacao: function (val) {
      this.calcular();
    }
  },
  methods: {
    calcular() {
      switch (this.operacao) {
        case 'soma':
          this.resultado = this.numero1 + this.numero2;
          break;
        case 'subtracao':
          this.resultado = this.numero1 - this.numero2;
          break;
        case 'multiplicacao':
          this.resultado = this.numero1 * this.numero2;
          break;
        case 'divisao':
          this.resultado = this.numero2 !== 0 ? this.numero1 / this.numero2 : 'Divisão por zero!';
          break;
      }
    }
  }
}
</script>

<style>
#app {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  border-radius: 8px;
  background-color: #f9f9f9;
}

input[type="number"], select {
  width: 100%;
  padding: 8px;
  margin: 10px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  font-size: 16px;
}

select {
  cursor: pointer;
}

h3 {
  color: #333;
  font-family: 'Arial', sans-serif;
}

button {
  width: 100%;
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

@media (max-width: 600px) {
  #app {
    width: 90%;
    margin: 20px auto;
  }
}
</style>

