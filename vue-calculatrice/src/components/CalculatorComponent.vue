<template>
  <div class="container mt-5">
    <h1 class="text-center">Calculatrice</h1>
    <OperationSelector v-model="operation" />
    <InputFields :value1="value1" :value2="value2" @updateValue1="value1 = $event" @updateValue2="value2 = $event" />
    <button class="btn btn-primary mt-3" @click="calculate">Calculer</button>
    <ResultDisplay :result="result" :error="error" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import OperationSelector from './components/OperationSelector.vue'
import InputFields from './components/InputFields.vue'
import ResultDisplay from './components/ResultDisplay.vue'

const operation = ref('+')
const value1 = ref('')
const value2 = ref('')
const result = ref('')
const error = ref('')

const calculate = () => {
  try {
    const num1 = parseFloat(value1.value)
    const num2 = parseFloat(value2.value)

    if (isNaN(num1) || isNaN(num2)) {
      throw new Error('Veuillez entrer des nombres valides')
    }

    switch (operation.value) {
      case '+':
        result.value = num1 + num2
        break
      case '-':
        result.value = num1 - num2
        break
      case '*':
        result.value = num1 * num2
        break
      case '/':
        if (num2 === 0) {
          throw new Error('Division par zéro impossible')
        }
        result.value = num1 / num2
        break
      default:
        throw new Error('Opération non valide')
    }
    error.value = ''
  } catch (err) {
    error.value = err.message
  }
}
</script>
