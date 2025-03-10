<template>
  <div>
    <MyHeader></MyHeader>
    <MyForm @updateTodoList="updateTodoList"></MyForm>
    <div>
      {{ todolist }}
    </div>
  </div>
</template>
<script setup>
import { reactive, ref } from "vue";
import MyHeader from "./components/MyHeader.vue";
import MyForm from "./components/MyForm.vue";
const todolist = ref([]);

const updateTodoList = (item) => {
  todolist.value.push(item);
};
</script>
