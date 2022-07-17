<script setup lang="ts">
import TodoItem from "./TodoItem.vue";
defineProps<{ todos: { id: number; text: string; isCompleted: boolean }[] }>();
</script>

<template>
  <div class="todo-list">
    <div v-for="todo in todos">
      <TodoItem :todo="todo" />
    </div>
  </div>
</template>

<style scoped>
.todo-list {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-top: 16px;
}
</style>
