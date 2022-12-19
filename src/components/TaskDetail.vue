<template>
  <section class="task-container-detail">
    <h1 class="task-title">PENDING</h1>
    <div v-for="task in tasksNotCompleted" :key="task.id">
      <TaskNotCompleted :task="task" />
    </div>
    <div class="working" v-if="tasksNotCompleted.length === 0">All has completed</div>
    <h1 class="task-title">COMPLETED</h1>
    <div v-for="task in tasksCompleted" :key="task.id">
      <TaskCompleted :task="task" />
    </div>
    <div class="working" v-if="tasksCompleted.length === 0">Nothing is completed</div>
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

.working {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  background-color: rgb(88, 88, 88, 0.2);
  height: 100px;
  font-size: 30px;
  border-radius: 20px;
}
</style>