<script setup>
import { computed, ref, watch } from "vue";

const todoData = ref(null);
const todoId = ref(1);

const fetchData = async () => {
  todoData.value = null;
  const data = await fetch(`https://jsonplaceholder.typicode.com/todos/${todoId.value}`);
  todoData.value = await data.json();
};

const addTodoId = () => todoId.value++;

fetchData();

watch(todoId, fetchData);
</script>

<template>
  <h1>todo id: {{ todoId }}</h1>
  <p v-if="!todoData">Loading ...</p>
  <pre v-else="todoData">
    {{ todoData }}
  </pre>

  <button @click="addTodoId">See todo on id: {{ todoId }}</button>
</template>
