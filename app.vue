<template>
  <div class="m-8 font-sans flex justify-center w-full">
    <div class="max-w-screen-sm w-full flex flex-col items-center space-y-4">
      <div class="flex justify-center">
        <h1 class="text-4xl">Todo</h1>
      </div>
      <!-- Create Task -->
      <div class="w-full">
        <div class="bg-gray-300/30 px-4 py-2 border rounded-t-md w-full">
          <p>Add a task</p>
        </div>
        <div class="p-4 border rounded-b-md space-y-2">
          <p>Item</p>
          <input
            v-model="newTodo"
            type="text"
            class="rounded-md border px-4 py-2 w-full text-sm"
            placeholder="What do you want to do ?"
          />
          <p class="text-sm">Enter what you want to procastinate</p>
          <button
            class="bg-blue-600 hover:bg-blue-400 text-white text-sm px-3 py-1.5 rounded-md"
            @click="createTodo"
          >
            Submit
          </button>
        </div>
      </div>
      <!-- Task List -->
      <div class="w-full">
        <div class="bg-gray-300/30 px-4 py-2 border rounded-t-md w-full">
          <p>Tasks</p>
        </div>
        <div class="p-4 border rounded-b-md space-y-2 w-full">
          <table class="w-full table-auto">
            <thead>
              <tr>
                <th>Item</th>
                <th>Status</th>
                <th class="!text-center">Action</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(todo, index) in todoList" :key="index">
                <td>{{ todo.item }}</td>
                <td
                  :class="[
                    todo.completed == 0 ? 'text-red-500' : 'text-green-500',
                  ]"
                >
                  {{ todo.completed == 0 ? "Not Complete" : "Completed" }}
                </td>
                <td class="flex justify-center">
                  <button
                    class="bg-blue-600 hover:bg-blue-400 text-white px-3 py-1 rounded-md mr-2"
                    @click="toggleCompleteTodo(todo)"
                  >
                    {{ todo.completed == 0 ? "Complete" : "Incomplete" }}
                  </button>
                  <button
                    class="bg-red-600 hover:bg-red-400 text-white px-3 py-1 rounded-md"
                    @click="deleteTodo(todo)"
                  >
                    Delete
                  </button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { Todo } from "./models/todo";

const url = "http://127.0.0.1:3000/api/todo";

const todoList = ref<Todo[]>([]);
const newTodo = ref<string>();

async function getTodo() {
  const res: any = await $fetch(url, {
    method: "GET",
  });

  todoList.value = res.data;
}

async function createTodo() {
  const res: any = await $fetch(url, {
    method: "POST",
    body: {
      item: newTodo.value,
      completed: 0,
    },
  });

  newTodo.value = "";

  await getTodo();
}

async function toggleCompleteTodo(todo: Todo) {
  const res: any = await $fetch(`${url}\\${todo.id}`, {
    method: "PUT",
    body: {
      item: todo.item,
      completed: todo.completed == 0 ? 1 : 0,
    },
  });

  await getTodo();
}

async function deleteTodo(todo: Todo) {
  const res: any = await $fetch(`${url}\\${todo.id}`, {
    method: "DELETE",
  });

  await getTodo();
}

onMounted(async () => {
  await getTodo();
});
</script>

<style scoped>
th {
  @apply text-start font-semibold text-sm;
}

td {
  @apply py-2 text-sm;
}
</style>
