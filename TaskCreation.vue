<template>
  <div>
    <input v-model="newTaskTitle" placeholder="Enter task title" />
    <button @click="addTask">Add Task</button>
    <div v-if="error" class="error">{{ error }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTaskTitle: '',
      error: '',
    };
  },
  methods: {
    addTask() {
      if (this.newTaskTitle.trim() === '') {
        this.error = 'Task title cannot be empty';
        return;
      }

      this.$emit('task-added', { id: Date.now(), title: this.newTaskTitle, completed: false });
      this.newTaskTitle = '';
      this.error = '';
    },
  },
};
</script>

<style scoped>
/* Scoped styles apply only to this component */

form {
  display: flex;
  align-items: center;
}

input {
  flex: 1;
  padding: 10px;
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
</style>

