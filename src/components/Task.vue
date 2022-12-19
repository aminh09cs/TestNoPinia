<template>
  <div class="task-container">
    <AddTask :tasks="tasks" @newTask="addNewTask" />
    <TaskDetail :tasksCompleted="tasksCompleted" :tasksNotCompleted="tasksNotCompleted" />
  </div>
</template>
<script setup>
//emit, provide, inject, props
import AddTask from './AddTask.vue'
import TaskDetail from './TaskDetail.vue';
import { ref, computed, provide } from 'vue';

//data
const tasks = ref([
  { id: 1, nameWork: "Drink Coffee", isCompleted: false, isProgress: false },
  { id: 2, nameWork: "Watch TV", isCompleted: false, isProgress: false },
  { id: 3, nameWork: "Coding", isCompleted: true, isProgress: false },
  { id: 4, nameWork: "Eat Lunch", isCompleted: false, isProgress: false },
  { id: 5, nameWork: "Play soccer", isCompleted: true, isProgress: false },
  { id: 6, nameWork: "Go to cinema", isCompleted: false, isProgress: false },
]);

const tasksCompleted = computed(() => {
  return tasks.value.filter(task => task.isCompleted === true);
})
const tasksNotCompleted = computed(() => {
  return tasks.value.filter(task => task.isCompleted === false);
})

provide('tasks', tasks);
const addNewTask = (data) => {
  tasks.value.push(data);
}
</script>

<style lang="scss">
.task-container {
  width: 70%;
  margin: 0 auto;
  padding: 50px;
  border-radius: 30px;
  background: #38404B;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}
</style>