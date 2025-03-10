<template>
  <div>
    <div>List of To do</div>
    <MyItemTodo
      v-for="item in myTodoList"
      :key="item.id"
      :task="item"
    ></MyItemTodo>
  </div>
</template>
<script setup>
import MyItemTodo from "./MyItemTodo.vue";

const props = defineProps(["myTodoList"]);
</script>
