<script setup lang="ts">
import { ref, provide } from "vue";
import AddTodo from "./components/AddTodo.vue";
import TodoList from "./components/TodoList.vue";

const todos = ref<{ id: number; text: string; isCompleted: boolean }[]>([]);

function addTodo(text: string) {
  todos.value.push({
    id: todos.value.length,
    text,
    isCompleted: false,
  });
}

provide("toggleTodo", function toggleTodo(id: number) {
  const todo = todos.value.find((todo) => todo.id === id);
  if (todo) {
    todo.isCompleted = !todo.isCompleted;
  }
});

provide("deleteTodo", function deleteTodo(id: number) {
  todos.value = todos.value.filter((todo) => todo.id !== id);
});
</script>

<template>
  <div class="container">
    <h1 class="title">Vue Todo App</h1>
    <AddTodo :add-todo="addTodo" />
    <TodoList :todos="todos" />
  </div>
</template>

<style scoped>
.title {
  text-align: center;
}
@media (max-width: 320px) {
  .container {
    padding-inline: 16px;
  }
}
</style>
