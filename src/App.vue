<script setup>

</script>


<template>
  <div id="app" class="container mt-5">
    <h2>Calculadora Aritmética</h2>
    <div class="form-group">
      <label for="num1">Número 1:</label>
      <input
        type="number"
        id="num1"
        v-model="num1"
        class="form-control"
        placeholder="Digite o primeiro número"
      />
    </div>
    <div class="form-group">
      <label for="num2">Número 2:</label>
      <input
        type="number"
        id="num2"
        v-model="num2"
        class="form-control"
        placeholder="Digite o segundo número"
      />
    </div>
    <div class="form-group">
      <label for="operation">Operação:</label>
      <select
        id="operation"
        v-model="operation"
        class="form-control"
      >
        <option value="+">Soma (+)</option>
        <option value="-">Subtração (-)</option>
        <option value="*">Multiplicação (×)</option>
        <option value="/">Divisão (÷)</option>
      </select>
    </div>

    <h3 class="mt-4">Resultado: {{ resultado }}</h3>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: 0,
      num2: 0,
      operation: '+', 
    };
  },
  computed: {
    
    resultado() {
      let res = 0;
      switch (this.operation) {
        case '+':
          res = parseFloat(this.num1) + parseFloat(this.num2);
          break;
        case '-':
          res = parseFloat(this.num1) - parseFloat(this.num2);
          break;
        case '*':
          res = parseFloat(this.num1) * parseFloat(this.num2);
          break;
        case '/':
          if (this.num2 === 0) {
            res = 'Não pode dividir por zero';
          } else {
            res = parseFloat(this.num1) / parseFloat(this.num2);
          }
          break;
      }
      return res;
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 400px;
  margin-top: 50px;
}

input[type="number"] {
  width: 100%;
}

select {
  width: 100%;
}

h3 {
  font-size: 1.5rem;
}
</style>
