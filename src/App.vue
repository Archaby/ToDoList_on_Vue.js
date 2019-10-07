<template>
  <div 
    id="app"
  >
    <img 
      alt="Vue logo" 
      src="./assets/logo.png"
    >
    <h1 
      class="mt-3 mb-3"
    >
      ToDoList
    </h1>
    <form>
      <div 
        class="form-row"
      >
        <div 
          class="w-50 mx-auto mt-3 mb-3"
        >
          <input 
            type="text" 
            class="form-control" 
            id="taskForm" 
            placeholder="task"
            maxlength="20" 
            required>
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
    <div class="w-50 mx-auto">
      <div 
        v-for="(value, index) in arrTasks"
        :key="index"
      >
        <TaskBlock 
          :messageTask="value.messageTask"
          :numberTask="value.numberTask"
        />
      </div>
    </div>    
  </div>
</template>

<script>
  import TaskBlock from './components/TaskBlock.vue'

export default {
  name: 'app',
  components: {
    TaskBlock
  },
  
  data() {
    return {
      taskFormRef: null,
      arrTasks: [],
      messageTaskFromChild: '',
      numberTask: undefined
    }
  },
  
  mounted() {
    this.taskFormRef = document.querySelector('#taskForm');
    this.$on('clickBtnForParent', obj => {
      this.messageTaskFromChild = obj.messageTask;
      if(obj.btnClick == 'change') {
       
        return; 
      }
      this.arrTasks.forEach((item, index, arr) => {
        console.log(item);
        if(item[numberTask] == obj[numberTask]) arr.splice(index+1,1);
      });
    });
  },  
  
  methods: {
    addTask() {
      if(this.taskFormRef.value) {
        this.arrTasks.push({});
        this.arrTasks[this.arrTasks.length - 1].messageTask = this.taskFormRef.value;
        this.arrTasks[this.arrTasks.length - 1].numberTask = this.arrTasks.length - 1;
        //console.log(this.arrTasks[this.arrTasks.length - 1].numberTask);
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
    text-align: center

  h1
    color: white
    text-align: center  
</style>
