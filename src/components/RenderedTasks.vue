<template>
  <div :key="task.id" v-for="task in tasks">
    <TaskCard
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      @delete-task="$emit('delete-task', task.id)"
      :task="task"
    />
  </div>
</template>

<script>
import TaskCard from "./TaskCard.vue";
export default {
  name: "RenderedTasks",
  props: {
    tasks: Array,
  },
  components: {
    TaskCard,
  },
  emits: ["delete-task", "toggle-reminder"],
};
</script>
