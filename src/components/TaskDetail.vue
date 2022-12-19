<template>
  <section class="task-container-detail">
    <h1 class="task-title">PENDING</h1>
    <div v-for="task in tasksNotCompleted" :key="task.id">
      <TaskNotCompleted :task="task" />
    </div>
    <h1 class="task-title">COMPLETED</h1>
    <div v-for="task in tasksCompleted" :key="task.id">
      <TaskCompleted :task="task" />
    </div>

  </section>
</template>
<script setup>
import { defineProps, onUpdated, ref, watch } from 'vue';

import TaskCompleted from './TaskCompleted.vue'
import TaskNotCompleted from './TaskNotCompleted.vue'

const props = defineProps([
  "tasksNotCompleted",
  "tasksCompleted"
])

//ref
// const tasksCompleted = ref([]);
// const tasksNotCompleted = ref([]);
// tasksCompleted.value = props.tasks.filter(task => task.isCompleted === true);
// tasksNotCompleted.value = props.tasks.filter(task => task.isCompleted === false);

// watch(() => {
//   props.tasks,
//     () => {
//       tasksCompleted.value = props.tasks.filter(task => task.isCompleted === true);
//       tasksNotCompleted.value = props.tasks.filter(task => task.isCompleted === false);
//     }
// })


</script>
<style lang="scss" scoped>
.task-container-detail {
  margin-top: 30px;

  .task-title {
    text-align: center;
    color: #94ADCF;
    font-size: 1.5rem;
    font-weight: 700;
    padding: 30px 0;
  }
}
</style>