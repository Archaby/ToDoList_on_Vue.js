<template>
  <div 
    class="block w-50 mt-3 mb-3"
  >

  </div>
</template>

<script>

export default {
  
  props: {
    messageTask: {
      type: String,
      default: '',
    }
  },
  
  data() {
    return {
      //taskFormRef: null,
      //arrTasks: []
    }
  },
  
  mounted() {
    //this.taskFormRef = document.querySelector('#taskForm');
  },  
  
  methods: {
    
  }

}
</script>

<style lang="sass">
    .block
        border-radius: 5px
</style>