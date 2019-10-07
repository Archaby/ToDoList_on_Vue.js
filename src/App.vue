<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <h1 class="mt-3 mb-3">ToDoList</h1>
    <form>
      <div class="form-row">
        <div class="col-md-4 mt-3 mb-3">
          <!-- <label for="taskForm">Task</label> -->
          <input type="text" class="form-control" id="taskForm" placeholder="Task" required>
        </div>
      </div>
      <button 
        class="btn btn-primary" 
        type="submit"
        @click="addTask"
      >
        Add task
      </button>  
    </form>
    <div>
      <div v-for="(value, index) in arrTasks"
          :key="index"
      >
        <p> {{ value.messageTask }} </p>
      </div>
    </div>    
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    // HelloWorld
  },
  
  data() {
    return {
      taskFormRef: null,
      arrTasks: []
    }
  },
  
  mounted() {
    this.taskFormRef = document.querySelector('#taskForm');
  },  
  
  methods: {
    addTask() {
      if(this.taskFormRef.value) {
        this.arrTasks.push({});
        this.arrTasks[this.arrTasks.length - 1].messageTask = this.taskFormRef.value;
        this.taskFormRef.value = '';  
      }
    }
  }

}
</script>

<style lang="sass">
  *
    margin: 0
    padding: 0
    box-sizing: border-box

  body
    background: url(assets/background.jpg) no-repeat center top / cover  

  #app
    border: 1px solid red

  h1
    color: white
    text-align: center  
</style>
