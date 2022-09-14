<template>
  <header>
    <h1>{{ title }}</h1>
    <AddTaskButton
      @button-click="$emit('toggle-add-task')"
      :text="showAddTask ? 'Close' : 'Add task'"
      :color="showAddTask ? 'red' : 'green'"
    />
  </header>
</template>

<script>
import AddTaskButton from "./AddTaskButton.vue";

export default {
  name: "AppHeader",
  props: {
    title: String,
    showAddTask: Boolean,
  },
  components: {
    AddTaskButton,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
