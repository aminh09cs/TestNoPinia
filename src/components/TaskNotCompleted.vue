<template>
  <div class="tasks-item">
    <div class=" task-item">
      <div class="task-item-left">
        <span class="task-item-icon" :class="task.isCompleted ? 'completed' : ''">

        </span>
        <div>{{ task.nameWork }}</div>
      </div>
      <BtnTask :task="task" />
    </div>
  </div>
</template>
<script setup>
import { defineProps, ref } from 'vue';
import BtnTask from './BtnTask.vue'
const props = defineProps({
  task: Object,
})

</script>

<style lang="scss" scoped >
.tasks-item {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;

  .task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 10px;

    width: 100%;
    background: #38404B;
    box-shadow: -5px 5px 10px rgba(48, 54, 64, 0.2),
      5px -5px 10px rgba(48, 54, 64, 0.2),
      -5px -5px 10px rgba(64, 74, 86, 0.9),
      5px 5px 13px rgba(48, 54, 64, 0.9),
      inset 1px 1px 2px rgba(64, 74, 86, 0.3),
      inset -1px -1px 2px rgba(48, 54, 64, 0.5);
    border-radius: 16px;
    font-family: 'Ubuntu';
    font-style: normal;
    font-weight: 500;
    font-size: 18px;

    padding: 10px;
    margin: 5px 0;
    line-height: 21px;
    color: #94ADCF;

    .task-item-left {
      display: flex;

      .task-item-icon {
        border-radius: 50%;
        width: 18px;
        height: 18px;
        border: 2.5px solid #94ADCF;
        margin-right: 10px;
        cursor: pointer;
      }
    }

  }
}

.completed {
  background-color: #94ADCF;
}
</style>

