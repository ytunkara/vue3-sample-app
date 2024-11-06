<template>
  <div>
    <h1>Vue 3 Sample Task App</h1>
    <input v-model="newTask" placeholder="Add a new task" />
    <button @click="addTask">Add Task</button>

    <ul>
      <li v-for="task in tasks" :key="task.id">
        <label>
          <input type="checkbox" v-model="task.completed" />
          <span :style="{ textDecoration: task.completed ? 'line-through' : 'none' }">{{ task.text }}</span>
        </label>
        <button @click="removeTask(task.id)">Remove</button>
      </li>
    </ul>

    <p>Tasks Completed: {{ completedTasks }} / {{ tasks.length }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [
        { id: 1, text: 'Learn Vue 3', completed: false },
        { id: 2, text: 'Create a sample app', completed: true }
      ]
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({
          id: this.tasks.length + 1,
          text: this.newTask.trim(),
          completed: false
        });
        this.newTask = '';
      }
    },
    removeTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id);
    }
  },
  computed: {
    completedTasks() {
      return this.tasks.filter(task => task.completed).length;
    }
  }
};
</script>

<style>
/* Add optional styling */
</style>