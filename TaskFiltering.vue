<template>
  <div>
    <label>Show:</label>
    <select v-model="selectedFilter" @change="filterChanged">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="incomplete">Incomplete</option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedFilter: 'all',
    };
  },
  methods: {
    filterChanged() {
      this.$emit('filter-changed', this.selectedFilter);
    },
  },
};
</script>

<style scoped>
/* Scoped styles apply only to this component */

label {
  font-size: 16px;
  margin-right: 10px;
}

select {
  padding: 5px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>

