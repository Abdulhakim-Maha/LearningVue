<template>
  <div class="container">
    <Header
      title="My Tasks"
      :showAddTask="showAddTask"
      @toggle-btn="toggleButton"
    />
    <div v-if="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    toggleButton() {
      this.showAddTask = !this.showAddTask;
    },
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => {
          return task.id !== id;
        });
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => {
        if (task.id === id) {
          return { ...task, reminder: !task.reminder };
        } else {
          return task;
        }
      });
    },
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctor Appointment",
        day: " 1/12/2564",
        reminder: true,
      },
      {
        id: 2,
        text: "Linear algebra Final",
        day: " 3/12/2564",
        reminder: true,
      },
      {
        id: 3,
        text: "Final Project",
        day: " 17/12/2564",
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
