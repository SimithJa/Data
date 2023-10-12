<template>
  <ul>
    <li v-for="task in tasks" :key="task.id">
      {{ task.title }}
      <button @click="deleteTask(task.id)">Delete</button>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    tasks: Array,
  },
  methods: {
    deleteTask(taskId) {
      this.$emit('task-deleted', taskId);
    },
  },
};
</script>

<style scoped>
/* Scoped styles apply only to this component */

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
</style>

