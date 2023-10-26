<script setup lang="ts">
  import { ref, computed, watch } from 'vue'

  const variable = ref(1)

  const computedProperty = computed(() => {
    return variable.value * 2
  })

  watch(computedProperty, (newValue, oldValue) => {
    console.log('computedProperty was ' + oldValue + '. Now it is ' + newValue + '.')
  })

  
</script>

<template>
  <button @click="variable++">Click me</button>
</template>