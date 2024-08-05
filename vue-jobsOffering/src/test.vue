<script setup>
import { ref, reactive } from "vue";

const type = reactive({
  tasks: ["Task one", "Task two", "Task three"],
  task: "",
});
const name = ref("mgmg");
const status = ref("active");

const toggleButton = () => {
  if (status.value === "active") {
    status.value = "pending";
  } else if (status.value === "pending") {
    status.value = "inactive";
  } else {
    status.value = "active";
  }
};

const deleteTask = (i) => {
  type.tasks.splice(i, 1);
};

const addTask = () => {
  if (type.task !== "") {
    type.tasks.push(type.task);
    type.task = "";
  }
};
</script>

<template>
  <h1>Vue Test</h1>

  <ul>
    <li v-for="(t, i) in type.tasks" :key="i">
      <span>{{ t }}</span>
      <button @click="deleteTask(i)">delete</button>
    </li>
  </ul>
  <input type="text" v-model="type.task" />
  <button @click="addTask">Add</button>
  <h1>
    <span>{{ name }}</span>
    <p v-if="status === 'active'">User Is Active</p>
    <p v-else-if="status === 'pending'">User Is Pending</p>
    <p v-else>User Is inActive</p>
  </h1>
  <button @click="toggleButton">Click me</button>
</template>
