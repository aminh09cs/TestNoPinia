<template>
  <div class="task-item-right">
    <span class="task-item-right-icon trash" @click="delTasks(props.task.id)">
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

const tasks = inject('tasks')
const delTasks = inject('delTasks');
//emit 
const onCompleted = () => {
  tasks.value.forEach((task) => {
    if (task.id === props.task.id) {
      task.isCompleted = !task.isCompleted;
    }
  })
}

</script>
<style lang="scss" scoped>
.task-item-right {
  display: flex;
  gap: 10px;

  .task-item-right-icon {
    cursor: pointer;

    &:hover {
      animation: rotation 0.2s infinite alternate;
    }
  }
}

//keyframe
@keyframes rotation {
  from {
    transform: rotate(-20deg);
  }

  to {
    transform: rotate(20deg);
  }
}
</style>