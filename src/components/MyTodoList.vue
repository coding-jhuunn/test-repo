<template>
  <div class="">
    <div>List of To do</div>
    <MyItemTodo
      v-for="item in myTodoList"
      :key="item.id"
      :task="item"
      @deleteItemTodo="deleteItemTodo"
    ></MyItemTodo>
  </div>
</template>
<script setup>
import { defineEmits } from "vue";
import MyItemTodo from "./MyItemTodo.vue";

const emit = defineEmits(["deleteItemTodo"]);
const deleteItemTodo = (index) => {
  emit("deleteItemTodo", index);
};

const props = defineProps(["myTodoList"]);
</script>
