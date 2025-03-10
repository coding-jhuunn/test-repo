<template>
  <div class="max-w-md mx-auto p-6 bg-white shadow-lg rounded-lg">
    <form @submit.prevent="submitForm" class="flex flex-col">
      <div>
        <label class="block font-medium">Title</label>
        <input
          v-model="titleTask"
          type="text"
          class="w-full p-2 border rounded-md"
        />
      </div>
      <div>
        <input v-model="priorityTask" type="checkbox" />
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
import { ref, reactive, defineEmits } from "vue";

const emit = defineEmits(["updateTodoList"]);

const submitForm = () => {
  emit("updateTodoList", {
    id: Date.now(),
    title: titleTask.value,
    priorityTask: priorityTask.value,
  });
};

const titleTask = ref("");
const priorityTask = ref(false);
</script>
