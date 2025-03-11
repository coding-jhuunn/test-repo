<template>
  <div class="p-6 bg-white shadow-lg rounded-lg">
    <form
      @submit.prevent="submitForm"
      class="flex flex-row justify-evenly items-center"
    >
      <div class="bg-red-50 flex flex-col h-12">
        <label class="block font-medium">Title</label>
        <input
          v-model="titleTask"
          type="text"
          class="border-b-2"
          placeholder="Input Here"
        />
      </div>
      <div
        class="bg-green-50 flex justify-evenly align-center items-center h-12"
      >
        <input v-model="priorityTask" type="checkbox" />
        <label class="font-medium">Priority</label>
      </div>
      <div class="">
        <button
          class="w-full bg-blue-500 text-white py-2 rounded-md hover:bg-blue-600"
        >
          Submit
        </button>
      </div>
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
