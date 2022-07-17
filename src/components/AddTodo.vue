<script setup lang="ts">
import { ref } from "vue";

defineProps<{ addTodo: (text: string) => void }>();

const todoText = ref("");
</script>

<template>
  <form
    @submit="
      (e) => {
        e.preventDefault();
        addTodo(todoText);
      }
    "
    class="add-todo-form"
  >
    <input
      v-model="todoText"
      type="text"
      name="todo"
      id="todo"
      placeholder="Enter your todo here..."
      className="input"
    />
    <button type="submit" className="add-todo-btn">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="{16}"
        height="{16}"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
        strokeWidth="{2}"
      >
        <path strokeLinecap="round" strokeLinejoin="round" d="M12 6v6m0 0v6m0-6h6m-6 0H6" />
      </svg>
    </button>
  </form>
</template>

<style scoped>
.add-todo-form {
  display: flex;
  gap: 8px;
}
.input {
  box-sizing: border-box;
  width: 100%;
  outline: none;
  border: none;
  padding: 8px;
  background-color: #eee;
  border-radius: 4px;
  box-shadow: 0 0 0 1px #d3d1d1;
}

.input:hover,
.input:focus {
  box-shadow: 0 0 0 1px #d3d1d1, 0 0 0 2px #d3d1d1;
}

.add-todo-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  cursor: pointer;
  border-radius: 4px;
  background: transparent;
  border: 1px solid #393e46;
  outline: none;
  padding: 4px;
  transition: color 0.2s ease-in-out, background-color 0.2s ease-in-out;
}

.add-todo-btn:hover {
  background: #393e46;
  color: #fff;
}
</style>
