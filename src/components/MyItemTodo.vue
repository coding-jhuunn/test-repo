<template>
  <div class="max-wd flex justify-between">
    <div class="flex">
      <div>
        {{ task.priorityTask }}
      </div>
      <div>
        {{ task.title }}
      </div>
    </div>
    <div>
      <button @click="deleteItem(task.id)">Delete</button>
    </div>
  </div>
  <!-- <div
    :class="{
      'border-r-20 ': task.priorityTask,
      'bg-gray-300 text-black': !task.priorityTask,
    }"
  >
    <div>
      <p>{{ task.title }}</p>
      <button>Delete</button>
    </div>
  </div> -->
</template>

<script setup>
import { defineEmits } from "vue";

defineProps(["task"]);
const emit = defineEmits(["deleteItemTodo"]);

const deleteItem = (index) => {
  console.log(index);
  emit("deleteItemTodo", index);
};
</script>
