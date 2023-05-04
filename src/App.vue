<script setup>
import { reactive } from 'vue';
  const estado = reactive({
    operacao: 'somar',
    valor1: 0,
    valor2: 0,
  })

  const somar = (valor1, valor2) => valor1 + valor2
  const subtrair = (valor1, valor2) => valor1 - valor2
  const multiplicar = (valor1, valor2) => valor1 * valor2
  const dividir = (valor1, valor2) => valor1 / valor2

  const qualOperacaofazer = () => {
    const { operacao } = estado

    switch(operacao) {
      case 'somar':
        return somar(estado.valor1, estado.valor2)
      case 'subtrair':
        return subtrair(estado.valor1, estado.valor2)
      case 'multiplicar':
        return multiplicar(estado.valor1, estado.valor2)
      case 'dividir':
        return dividir(estado.valor1, estado.valor2).toFixed(1)
      default:
        return operacao
    }
    
  }

</script>

<template>
  <div class="container mt-4">
    <h1>Calculadora Vue</h1>
    <form class="row gap-3 mt-4">
      
      <input @keyup="evento => estado.valor1 = Number(evento.target.value)" class="form-control col" required type="number">
      <input @keyup="evento => estado.valor2 = Number(evento.target.value)" class="form-control col" required type="number">

      <select @change="evento => estado.operacao = evento.target.value" class="col-3 bg-primary rounded text-light">
        <option value="somar">Somar</option>
        <option value="subtrair">Subtrair</option>
        <option value="multiplicar">Multiplicar</option>
        <option value="dividir">Dividir</option>
      </select>
    </form>

    <div v-if="estado.valor2 > 0" class="text-center mt-4">resultado = ) {{ qualOperacaofazer() }}</div>
    <div v-else class="text-center mt-4">Digite um numero</div>
  </div>
</template>

<style scoped>

</style>
