<template>
  <div class="container">
    <Header title="Task tracker" />
    <div v-if="showAddTask">
      <AddTask  @add-task="addTask" />
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask"

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
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if (confirm("Are you sure you want to delete?")) {
        this.tasks = this.tasks.filter((task) => task.id!==id);
      }
    },
    toggleReminder(id){
      //console.log(id);
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
      //checking if task.id is equal to id being passed and if it is, return an
      //array of objects with the initial task properties spread across the initial task,
      //then set the reminder to whatever the oposite of the current task reminder else return initial task
    }
  }, 
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Car meet with the boys",
        day: "July 9th at 3:00pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Meeting with client",
        day: "July 9th at 8:00am",
        reminder: false,
      },
      {
        id: 3,
        text: "Hiking Everest",
        day: "July 12th at 6:00am",
        reminder: true,
      },
      {
        id: 4,
        text: "Responding to emails",
        day: "July 9th at 2:00pm",
        reminder: true,
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
/* .deleteBtn{
  display: inline-block;
  background: red;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
} */
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
/* .deleteBtn:active{
  transform:scale(0.98)
} */
.btn-block {
  display: block;
  width: 100%;
}
</style>
