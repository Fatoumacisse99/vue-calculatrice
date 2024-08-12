<template>
  <div class="mb-3">
    <label class="form-label">Entrez les valeurs :</label>
    <div class="input-group mb-2">
      <input 
        type="number" 
        class="form-control" 
        placeholder="Valeur 1" 
        v-model="localValue1"
        @input="$emit('updateValue1', localValue1)"
      />
      <input 
        type="number" 
        class="form-control" 
        placeholder="Valeur 2" 
        v-model="localValue2"
        @input="$emit('updateValue2', localValue2)"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const props = defineProps(['value1', 'value2'])

const localValue1 = ref(props.value1)
const localValue2 = ref(props.value2)

watch(() => props.value1, (newVal) => localValue1.value = newVal)
watch(() => props.value2, (newVal) => localValue2.value = newVal)
</script>
