<template>
  <div id="home">
    <section id="section-create-task">
      <h1>Todo List</h1>
      <p>Build a Simpole Todo List using Vue JS</p>
      <div class="create-task">
        <input
          type="text"
          placeholder="Add a new task"
          @keyup.enter="addTask()"
          v-model.trim="taskInput"
        />
        <button class="btn-addtask" @click="addTask()">Add</button>
      </div>
      <TaskListComponent @OnDeleteTask="deleteTask" :taskLists="taskLists" />
    </section>
  </div>
</template>

<script>
import TaskListComponent from '@/components/TaskListComponent.vue';
import { v4 as uuid } from 'uuid';
export default {
  name: 'HomeView',
  components: {
    TaskListComponent,
  },
  data() {
    return {
      taskLists: [
        { id: 1, title: 'Task 1', complated: true },
        { id: 2, title: 'Task 2', complated: false },
        { id: 3, title: 'Task 3', complated: false },
      ],
      taskInput: '',
    };
  },
  methods: {
    addTask() {
      // console.log('Add Task Succeed!');
      this.taskLists.push({
        id: uuid(),
        title: this.taskInput,
        complated: false,
      });
      this.taskInput = '';
    },
    deleteTask(id) {
      this.taskLists = this.taskLists.filter((list) => list.id !== id);
    },
  },
};
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700&display=swap');
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}
:root {
  --main-color: #2288ff;
  --second-color: #192f6a;
  --text-color: #314862;
  --bg-color: #fff;
  --box-shadow: 2px 2px 18px rgb(14 52 54 / 15%);
}

body {
  background-color: var(--bg-color);
  color: var(--text-color);
}
section {
  width: 100%;
  height: 100vh;
  padding-top: 2rem;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
section h1 {
  font-size: 2rem;
  color: var(--main-color);
  text-transform: uppercase;
  margin-bottom: 0.5rem;
}
section h1 ~ p {
  margin-bottom: 2rem;
}
section .create-task {
  display: flex;
  justify-content: center;
  align-items: center;
  max-width: 480px;
}
section .create-task input {
  appearance: none;
  border: none;
  outline: none;
  font-size: 1.5rem;
  color: var(--text-color);
  background-color: var(--bg-color);
  border-bottom: 1px solid var(--bg-color);
  padding: 0.5rem 0;
  margin: 0;
  transition: 0.4s;
}
section .create-task input:focus {
  border-bottom-color: var(--main-color);
}
section .create-task button {
  appearance: none;
  outline: none;
  font-size: 1.5rem;
  font-weight: 700;
  text-transform: uppercase;
  color: var(--main-color);
  background-color: var(--bg-color);
  border: 1px solid var(--main-color);
  border-radius: 0.5rem;
  padding: 0.5rem 1rem;
  margin-left: 1rem;
  cursor: pointer;
}
section .create-task button:hover {
  background-color: var(--main-color);
  color: var(--bg-color);
  box-shadow: var(--box-shadow);
}
section .tasks {
  width: 40%;
  min-width: 480px;
  margin-top: 2rem;
}
section .tasks .group {
  display: flex;
  align-items: center;
}
section .tasks .group .content {
  margin-left: 1rem;
}
section .tasks .task-list {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: var(--bg-color);
  border-radius: 0.5rem;
  box-shadow: var(--box-shadow);
  padding: 1rem;
  margin-bottom: 0.5rem;
}
input[type='checkbox'] {
  appearance: none;
  outline: none;
  height: 30px;
  width: 30px;
  background-color: #e5e5e5;
  border-radius: 5px;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}
input[type='checkbox']:after {
  content: '\f00c';
  font-family: 'Font Awesome\ 5 Free';
  font-size: 1.2rem;
  font-weight: 900;
  color: var(--bg-color);
  display: none;
}
input[type='checkbox']:hover {
  background-color: #c5c5c5;
  box-shadow: var(--box-shadow);
}
input[type='checkbox']:checked {
  background-color: rgb(47, 214, 111);
}
input[type='checkbox']:checked:after {
  display: block;
}
section .tasks .task-list .group .content {
  font-size: 1rem;
  font-weight: 600;
}
section .tasks .task-list button {
  appearance: none;
  border: none;
  outline: none;
  color: var(--bg-color);
  background-color: crimson;
  font-size: 0.875rem;
  font-weight: bold;
  text-transform: uppercase;
  padding: 0.5rem 1rem;
  border-radius: 5px;
  margin-left: 0.5rem;
  cursor: pointer;
}
section .tasks .task-list button:hover {
  box-shadow: 2px 2px 18px rgb(220 20 60 / 15%);
}
</style>
