<template>
  <h1>To Do List:</h1>
  <!-- <p>Find your task:</p>
  <input v-model="input" type="text" placeholder="Type the task here" />-->
  <ItemFilter :todos="todos" @update:filtered="filteredTasks = $event" />
  <p>Current tasks:</p>
  <ul>
    <li
      v-if="filteredTasks.length > 0"
      v-for="(todo, index) in filteredTasks"
      :key="index"
    >
      {{ todo }}
    </li>
    <li v-else>No results</li>
  </ul>
</template>

<script setup lang="ts">
import { computed, ref } from "vue";
import ItemFilter from "./ItemFilter.vue";

const todos = ref<string[]>(["Task 1", "Task 2", "Task 3", "Task 4", "Task 5"]);

const filteredTasks = ref<string[]>([]);
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
p {
  font-size: 1.5em;
}
li {
  font-size: 1.25rem;
}
</style>
