<script setup>
import { ref } from 'vue'

const counter = ref(0)
</script>

<template>
  <div class="container pt-5">
    <div class="card center">
      <h1>Counter: {{ counter }}</h1>
      <div>
        <button class="btn pimary" @click="counter++">+</button>
        <button class="btn danger" @click="counter--">-</button>
      </div>
    </div>
  </div>
</template>
