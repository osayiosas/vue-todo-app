<script setup>
import { ref } from 'vue'

const newTask = ref('')
const tasks = ref([])

const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push(newTask.value)
    newTask.value = ''
  }
}

const removeTask = (index) => {
  tasks.value.splice(index, 1)
}
</script>

<!-- todo app -->

<template>
  <div class="todo-ap">
    <div class="task-input">
      <input type="text" v-model="newTask" @keyup.enter="addTask" placeholder="Add a new task" />
      <button @click="addTask">Add To Do</button>
    </div>
      <ul class="task-list">
    <li v-for="(task, index) in tasks" :key="index" class="task-item">
      <span>{{ task }}</span>
       <button @click="removeTask(index)" class="remove-btn">Remove</button>
    </li>
   
  </ul>
  </div>

  <!-- Rendering all th task -->


</template>

<style scoped>
.todo-ap {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.app-title {
  font-size: 24px;
  margin-bottom: 20px;
  text-align: center;
  color: #333;
}

.task-input {
  display: flex;
  gap: 10px;
}

.task-input input {
  flex: 1;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
button {
    padding: 10px 20px;
    font-size: 16px;
    background-color: #898c90;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}
button:hover {
    background-color: #cddcef;
}

.task-list {
  margin-top: 20px;
  padding: 0;
  list-style: none;
}
.task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    margin: 8px 0;
    background-color: #f5efef;
    border: 1px solid #ddd;
    border-radius: 4px;
}

.remove-btn {
    padding: 5px 10px;
    font-size: 14px;
    background-color: #5e4542;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}
.remove-btn:hover {
    background-color: #cddcef;
}
</style>
