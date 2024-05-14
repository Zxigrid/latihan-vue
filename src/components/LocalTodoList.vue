<script setup>
import { ref, computed } from "vue";

const hideCompleted = ref(false);
const newTodo = ref("");
let id = 0;
const todos = ref([
  { id: id++, text: "Learn HTML", done: true },
  { id: id++, text: "Learn JavaScript", done: false },
  { id: id++, text: "Learn Vue", done: false },
]);

const addNewTodo = () => {
  todos.value.push({ id: id++, text: newTodo.value });
  newTodo.value = "";
};

const removeTodo = (todo) => (todos.value = todos.value.filter((t) => todo !== t));

const filteredTodos = computed(() =>
  hideCompleted.value ? todos.value.filter((t) => !t.done) : todos.value
);
</script>

<template>
  <h1>Todo List:</h1>
  <form for="newTodo" @submit.prevent="addNewTodo">
    <input v-model="newTodo" type="text" required />
    <button type="submit">Add</button>
  </form>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id" :class="{ done: todo.done }">
      <input type="checkbox" v-model="todo.done" /> {{ todo.text }}
      <button @click="removeTodo(todo)">X</button>
    </li>
    <li v-if="newTodo">{{ newTodo }}</li>
  </ul>
  <button type="button" @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? "Show All" : "Hide Completed" }}
  </button>
</template>
