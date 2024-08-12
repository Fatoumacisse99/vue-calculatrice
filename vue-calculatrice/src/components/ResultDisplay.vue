<template>
  <div v-if="error" class="alert alert-danger mt-3">
    {{ error }}
  </div>
  <div v-else-if="result !== ''" class="alert alert-success mt-3">
    Résultat : {{ result }}
  </div>
</template>

<script setup>
const props = defineProps(['result', 'error'])
</script>
