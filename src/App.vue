<template>
  <div class="container">
    <AppHeader
      @toggle-add-task="toggleAddTaskForm"
      title="Task Tracker"
      :showAddTaskForm="showAddTaskForm"
    />
    <div v-show="showAddTaskForm">
      <AddTaskForm @add-task="addTask" />
    </div>
    <RenderedTasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import RenderedTasks from "./components/RenderedTasks.vue";
import AddTaskForm from "./components/AddTaskForm.vue";

export default {
  name: "App",
  components: {
    AppHeader,
    RenderedTasks,
    AddTaskForm,
  },
  data() {
    return {
      tasks: [],
      showAddTaskForm: false,
    };
  },
  methods: {
    toggleAddTaskForm() {
      this.showAddTaskForm = !this.showAddTaskForm;
    },
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Task 1",
        day: "tasks day 1",
        reminder: true,
      },
      {
        id: 2,
        text: "Task 2",
        day: "tasks day 2",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
