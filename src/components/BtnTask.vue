<template>
  <div class="task-item-right">
    <span class="task-item-right-icon trash" @click="onRemove">
      <font-awesome-icon icon="fa-solid fa-trash" />
    </span>
    <span class="task-item-right-icon" @click="onCompleted">
      <font-awesome-icon icon="fa-solid fa-check" />
    </span>
  </div>
</template>
<script setup>
import { defineProps, inject } from 'vue';
//props
const props = defineProps([
  "task"
])

const tasks = inject('tasks');
//emit 
const onCompleted = () => {
  tasks.value.forEach((task) => {
    if (task.id === props.task.id) {
      task.isCompleted = !task.isCompleted;
    }
  })
}
const onRemove = () => {
  // tasks.value.forEach(task => {
  //   if (task.id === props.task.id) {
  //     console.log(task.id, props.task.id);
  //   }
  // });
  const id = props.task.id;
  console.log(tasks.value);
  tasks.value.filter(task => task.id !== id)
  console.log(tasks.value);
}
</script>
<style lang="scss" scoped>
.task-item-right {
  display: flex;
  gap: 10px;

  .task-item-right-icon {
    cursor: pointer;
  }
}
</style>