<template>
  <div class="form-container">
    <h2>📦 Pack Calculator</h2>

    <!-- Add Pack Size -->
    <form @submit.prevent="addPackSize">
      <label>Add Pack Size:</label>
      <input type="number" v-model.number="newPackSize" min="1" required/>
      <button type="submit">Add</button>
    </form>

    <!-- Show Pack Sizes as List -->
    <div v-if="packSizes.length">
      <h4>Pack Sizes:</h4>
      <ul>
        <li v-for="(size, index) in packSizes" :key="index">
          {{ size }}
          <button @click="removePackSize(index)">❌</button>
        </li>
      </ul>
    </div>

    <!-- Input for items -->
    <label>Items:</label>
    <input type="number" v-model.number="items" min="1" required/>

    <!-- Calculate Button -->
    <button @click="submit">Calculate</button>

    <!-- Result Table -->
    <div v-if="result && Object.keys(result.packs).length">
      <h3>Result:</h3>
      <table border="1">
        <thead>
        <tr>
          <th>Pack</th>
          <th>Quantity</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="(quantity, pack) in result.packs" :key="pack">
          <td>{{ pack }}</td>
          <td>{{ quantity }}</td>
        </tr>
        </tbody>
      </table>
      <p><strong>Total Items:</strong> {{ result.total_items }}</p>
      <p><strong>Total Packs:</strong> {{ result.total_packs }}</p>
    </div>
  </div>
</template>

<script setup>
import {ref} from 'vue'
import axios from 'axios'

const items = ref(0)
const newPackSize = ref(null)
const packSizes = ref([])
const result = ref(null)

const addPackSize = () => {
  if (newPackSize.value && !packSizes.value.includes(newPackSize.value)) {
    packSizes.value.push(newPackSize.value)
    newPackSize.value = null
  }
}

const removePackSize = (index) => {
  packSizes.value.splice(index, 1)
}

const API_URL = import.meta.env.VITE_API_URL || 'http://localhost:8080'

const submit = async () => {
  if (!items.value || packSizes.value.length === 0) {
    alert("Please enter items and at least one pack size.")
    return
  }

  try {
    const res = await axios.post(`${API_URL}/calculate`, {
      items: items.value,
      pack_sizes: packSizes.value,
    })
    result.value = res.data
  } catch (err) {
    result.value = { error: err.message }
  }
}

</script>

<style scoped>
.form-container {
  max-width: 600px;
  margin: auto;
  padding: 2rem;
  font-family: sans-serif;
}

input {
  display: block;
  width: 100%;
  margin-bottom: 0.5rem;
  padding: 0.5rem;
}

button {
  margin-bottom: 1rem;
  padding: 0.5rem 1rem;
}

table {
  width: 100%;
  margin-top: 1rem;
  border-collapse: collapse;
}

td, th {
  padding: 0.5rem;
  text-align: center;
}

ul {
  list-style: none;
  padding-left: 0;
}

li {
  margin-bottom: 0.25rem;
}
</style>
