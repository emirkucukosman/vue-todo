<script setup lang="ts">
import { inject } from "vue";
defineProps<{ todo: { id: number; text: string; isCompleted: boolean } }>();
const textDecoration = (isCompleted: boolean) => (isCompleted ? "line-through" : "none");
const handleToggleTodo = inject("toggleTodo") as (id: number) => void;
const handleDeleteTodo = inject("deleteTodo") as (id: number) => void;
</script>

<template>
  <div class="todo-item">
    <span :style="{ textDecoration: textDecoration(todo.isCompleted) }">
      {{ todo.text }}
    </span>
    <div className="todo-item-actions">
      <button
        className="action-btn"
        @click="
          {
            handleToggleTodo(todo.id);
          }
        "
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          strokeWidth="{2}"
          style="width: 18px; height: 18px"
        >
          <path
            v-if="todo.isCompleted"
            strokeLinecap="round"
            strokeLinejoin="round"
            d="M6 18L18 6M6 6l12 12"
          />
          <path v-else strokeLinecap="round" strokeLinejoin="round" d="M5 13l4 4L19 7" />
        </svg>
      </button>
      <button
        className="action-btn"
        @click="
          {
            handleDeleteTodo(todo.id);
          }
        "
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke="#ff0000"
          strokeWidth="{2}"
          style="width: 18px; height: 18px"
        >
          <path
            strokeLinecap="round"
            strokeLinejoin="round"
            d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"
          />
        </svg>
      </button>
    </div>
  </div>
</template>

<style scoped>
.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 8px;
  border-radius: 4px;
  background-color: #fff;
  box-shadow: 0 0 0 1px #d3d1d1;
  animation: fadeIn 0.2s ease-in-out;
  transform-origin: left;
}

.todo-item-actions {
  display: flex;
  align-items: center;
}

.action-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  border: none;
  outline: none;
  background: transparent;
  padding: 4px;
  border-radius: 50%;
  transition: background-color 0.1s ease-in-out;
}

.action-btn:hover {
  background: #f4f4f4;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: scaleX(0);
  }
  to {
    opacity: 1;
    transform: scaleX(1);
  }
}
</style>
