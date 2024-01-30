<script>
export default {
  name: 'App', 
  data(){
    return {
      newTask: '',
      error: false,
      tasks: [
        'Learn php',
        'Learn html',
        'Learn css',
        'Learn js',
        'Learn laravel',
      ]
    }
  },
  methods: {
    /* Method ( a function inside an object) syntax ES6 */
    addTask(){
      console.log('add the new task to the array of tasks', this.newTask);
      if(this.newTask.length > 5) {
        this.error = false;
        this.tasks.unshift(this.newTask);
        this.newTask = '';
      } else {
        this.error = 'The task must be at least 5 characters long'
      }
    },
    removeTask(i){
      this.tasks.splice(i,1)
    }
  }
}
</script>

<template>
 

 <div class="container my-4">
   <div class="card p-3">
    <h2>Tasks</h2>

    <div class="input-group mb-3">
      <input type="text" v-model="newTask" @keyup.enter="addTask">
      <button class="btn btn-dark" @click="addTask">Add</button>
    </div>

    <span class="text-danger" v-if="error">{{ error  }}</span>

    <ul class="list-group" v-if="tasks.length > 0">
      <li class="list-group-item d-flex justify-content-between" v-for="(task, index) in tasks">
        {{ task }}
        <span @click="removeTask(index)">X</span>
      </li>
    </ul>
    <p v-else>
      Nothing left relax! 😎
    </p>
  </div>
 </div>
</template>

<style>

.card:hover {
  background-color: black;
  cursor: progress;
}
</style>
