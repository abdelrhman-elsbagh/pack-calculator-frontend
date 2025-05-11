<template>
  <div>
    <button @click="showDocs = !showDocs" style="margin-bottom: 1rem;">
      {{ showDocs ? '← Back to Calculator' : '📘 API Docs' }}
    </button>

    <ApiDocs v-if="showDocs" />
    <CalculatorForm v-else />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import CalculatorForm from './components/CalculatorForm.vue'
import ApiDocs from './components/ApiDocs.vue'

const showDocs = ref(false)
</script>
