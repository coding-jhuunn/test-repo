<template>
  <div>
    <MyHeader></MyHeader>
    <div class="flex flex-col justify-center items-center">
      <MyForm class="m-5 border-1" @updateTodoList="updateTodoList"></MyForm>
      <div>
        <button @click="IsSorted = !IsSorted">
          {{ IsSorted ? "Sort" : "Sorted" }}
        </button>
      </div>

      <MyTodoList
        class="m-5 border-1"
        :myTodoList="IsSorted ? todolist : sortTask"
        @deleteItemTodo="deleteItemTodo"
        @toggleItemTodo="toggleItemTodo"
      ></MyTodoList>
    </div>
  </div>
</template>
<script setup>
import { computed, ref } from "vue";
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
const IsSorted = ref(true);

const sortTask = computed(() => {
  return [...todolist.value].sort((a, b) => {
    return IsSorted.value
      ? a.priorityTask - b.priorityTask
      : b.priorityTask - a.priorityTask;
  });
});

const updateTodoList = (item) => {
  todolist.value.push(item);
};
const deleteItemTodo = (item) => {
  todolist.value = todolist.value.filter((task) => task.id !== item);
};
const toggleItemTodo = (item) => {
  console.log("toggle");
  const task = todolist.value.find((task) => task.id === item);
  if (task) {
    task.priorityTask = !task.priorityTask;
  }
};
</script>
