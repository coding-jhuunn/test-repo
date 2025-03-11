<template>
  <div>
    <MyHeader></MyHeader>
    <div class="flex flex-col justify-center items-center">
      <MyForm class="m-5 border-1" @updateTodoList="updateTodoList"></MyForm>
      <MyTodoList
        class="m-5 border-1"
        :myTodoList="todolist"
        @deleteItemTodo="deleteItemTodo"
      ></MyTodoList>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import MyHeader from "./components/MyHeader.vue";
import MyForm from "./components/MyForm.vue";
import MyTodoList from "./components/MyTodoList.vue";
const todolist = ref([
  {
    id: 1,
    title: "Clean my Room",
    priorityTask: true,
  },
  {
    id: 2,
    title: "Read books",
    priorityTask: false,
  },
  {
    id: 3,
    title: "Serve Files",
    priorityTask: true,
  },
  {
    id: 4,
    title: "Take a bath",
    priorityTask: false,
  },
]);

const updateTodoList = (item) => {
  todolist.value.push(item);
};
const deleteItemTodo = (item) => {
  todolist.value = todolist.value.filter((task) => task.id !== item);
};
</script>
