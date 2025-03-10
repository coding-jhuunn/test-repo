<template>
  <div class="max-w-md mx-auto p-6 bg-white shadow-lg rounded-lg">
    <form @submit.prevent="submitForm" class="flex flex-col">
      <div>
        <label class="block font-medium">Title</label>
        <input
          v-model="itemTodo.title"
          type="text"
          class="w-full p-2 border rounded-md"
        />
      </div>
      <div>
        <input v-model="itemTodo.priority" type="checkbox" />
        <label class="font-medium">Priority</label>
      </div>
      <button
        class="w-full bg-blue-500 text-white py-2 rounded-md hover:bg-blue-600"
      >
        Submit
      </button>
    </form>
  </div>
</template>
<script setup>
import { reactive } from "vue";

const submitForm = () => {
  console.log(itemTodo);
};
const itemTodo = reactive([
  {
    title: "",
    priority: false,
  },
]);
</script>
