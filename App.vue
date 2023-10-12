<template>
  <div id="app">
    <h1>Task List</h1>
    <task-creation @task-added="addTask"></task-creation>
    <task-filtering @filter-changed="updateFilter"></task-filtering>
    <task-list :tasks="filteredTasks" @task-deleted="deleteTask"></task-list>
  </div>
</template>

<script>
import TaskCreation from './components/TaskCreation.vue';
import TaskFiltering from './components/TaskFiltering.vue';
import TaskList from './components/TaskList.vue';

export default {
  data() {
    return {
      tasks: [],
      filter: 'all',
    };
  },
  computed: {
    filteredTasks() {
      if (this.filter === 'all') {
        return this.tasks;
      } else if (this.filter === 'completed') {
        return this.tasks.filter(task => task.completed);
      } else {
        return this.tasks.filter(task => !task.completed);
      }
    },
  },
  methods: {
    addTask(newTask) {
      this.tasks.push(newTask);
    },
    deleteTask(taskId) {
      this.tasks = this.tasks.filter(task => task.id !== taskId);
    },
    updateFilter(newFilter) {
      this.filter = newFilter;
    },
  },
  components: {
    TaskCreation,
    TaskFiltering,
    TaskList,
  },
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

h1 {
  color: #333;
  font-size: 24px;
  margin-bottom: 20px;
}

input {
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  background-color: #007BFF;
  color: #fff;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background-color: #0056b3;
}

.error {
  color: red;
  font-size: 14px;
  margin-top: 5px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 10px;
  margin: 5px 0;
  background-color: #f9f9f9;
}

li button {
  background-color: #dc3545;
  color: #fff;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
  font-size: 14px;
  border-radius: 4px;
}

li button:hover {
  background-color: #a52d38;
}

select {
  padding: 5px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

</style>

