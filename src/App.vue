<script setup>
import { computed, ref, watch } from "vue";
import LocalTodoList from "./components/LocalTodoList.vue";
import ApiTodoList from '@/components/ApiTodoList.vue';
import Greeting from "./components/Greeting.vue";

const resMsg = ref('No response yet');
</script>

<template>
  <section>
    <LocalTodoList/>
  </section>
  
  <section style="margin-top: 5rem">
    <ApiTodoList/>
  </section>
  
  <section style="margin-top: 5rem">
    <Greeting name="World" @response="(msg) => resMsg = msg" >
      punya children :)
    </Greeting>
    <p>{{ resMsg }}</p>
  </section>
</template>

<style>
.done {
  text-decoration: line-through;
}
</style>
