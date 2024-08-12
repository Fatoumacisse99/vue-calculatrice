<template>
  <div class="mb-3">
    <label class="form-label">Choisissez une opération :</label>
    <div>
      <div class="form-check form-check-inline" v-for="op in operations" :key="op.value">
        <input 
          class="form-check-input" 
          type="radio" 
          :id="op.value" 
          :value="op.value" 
          v-model="selectedOperation"
          @change="emitOperation"
        />
        <label class="form-check-label" :for="op.value">{{ op.label }}</label>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const selectedOperation = ref('+')
const emit = defineEmits(['update:modelValue'])

watch(selectedOperation, (newVal) => {
  emit('update:modelValue', newVal)
})

const operations = [
  { value: '+', label: 'Addition' },
  { value: '-', label: 'Soustraction' },
  { value: '*', label: 'Multiplication' },
  { value: '/', label: 'Division' }
]
</script>
