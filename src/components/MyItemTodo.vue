<template>
  <div>
    <p>{{ task.title }}</p>
    <p v-show="task.priorityTask">priority</p>
  </div>
</template>

<script setup>
defineProps(["task"]);
</script>
