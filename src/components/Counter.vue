<template>
  <h1>Counter</h1>
  <p>Current Count: {{ count }}</p>
  <button id="increment" @click="increment">Increment</button>
  <button id="decrement" @click="decrement">Decrement</button>
  <button class="reset" @click="reset">Reset</button>
</template>

<script setup lang="ts">
import { ref, watch } from "vue";

//loading count from memory
const memory = localStorage.getItem("count");
const count = ref(memory ? Number(memory) : 0);

//localstorage gets updated after each change
watch(count, (newValue) => {
  localStorage.setItem("count", String(newValue));
});

function increment() {
  count.value++;
}
function decrement() {
  count.value--;
}
//reset the count and the localstorage
function reset() {
  count.value = 0;
  localStorage.removeItem("count");
}
</script>

<style scoped lang="scss">
h1 {
  font-size: 2em;
  margin-bottom: 10px;
}

button {
  margin: 5px;
  padding: 10px;
  font-size: 1em;
}
.reset {
  background-color: red;
}
</style>
