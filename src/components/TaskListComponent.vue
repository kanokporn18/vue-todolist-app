<template>
  <div class="tasks" v-for="taskList in taskLists" :key="taskList.id">
    <div class="task-list">
      <div class="group">
        <input type="checkbox" v-model="taskList.complated" />
        <div class="content">{{ taskList.title }}</div>
      </div>
      <button class="delete" @click="$emit('OnDeleteTask', taskList.id)">
        Delete
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TaskListComponent',
  props: ['taskLists'],
};
</script>

<style></style>
