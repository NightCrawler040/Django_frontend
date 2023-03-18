<script setup>
import {ref} from "vue";
import axios from "axios";
import {onMounted} from "vue";


const isLoaded = ref(false)
const products = ref([])
onMounted(async () => {
  const req = await axios.get('http://127.0.0.1:8000/api/products/')
  products.value =req.data.results
  isLoaded.value = true
})

</script>

<template>
  <h1>Home</h1>
  <div v-if="isLoaded">
    <ul>
      <li v-for="product in products" :key="product.id">
        {{product.title}}
      </li>
    </ul>
  </div>
  <div v-else>
    <p>Loading...</p>
  </div>
</template>


