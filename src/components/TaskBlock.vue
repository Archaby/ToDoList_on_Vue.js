<template>
  <div 
    class="block w-100 mx-auto d-flex mt-5 mb-3"
  >
    <!-- <div class="form-check">
        <input class="form-check-input" type="checkbox" id="gridCheck1">
    </div> -->
    <div
        class="d-flex"
    >
        <input class="form-check-input" type="checkbox" id="gridCheck1">
        <p> 
            {{ messageTask }} 
        </p>    
    </div>
    <div
        class="d-flex"    
    >   
        <div>
            <button 
                type="button" 
                class="btn btn-warning"
                @click="btnChange"
            >
                    To change
            </button>
        </div>
        <div>    
            <button 
                type="button" 
                class="btn btn-danger"
                @click="btnRemove"
            >
                    Remove
            </button>
        </div>        
    </div>      
  </div>
</template>

<script>

export default {
  
  props: {
    messageTask: {
      type: String,
      default: '',
    },
    numberTask: {
      type: Number,
      default: undefined,  
    }
    // btnClick: {
    //   type: String,
    //   default: '',
    // }
  },
  
  data() {
    return {
      btnClick: ''
      //taskFormRef: null,
      //arrTasks: []
    }
  },
  
  mounted() {
    //this.taskFormRef = document.querySelector('#taskForm');
  },  
  
  methods: {
      
      btnChange() {
        this.btnClick = 'change';
        this.whitchBtnClick();    
      },

      btnRemove() {
        this.btnClick = 'remove';
        this.whitchBtnClick();
        console.log(this.numberTask);    
      },

      whitchBtnClick() {
        this.$parent.$emit('clickBtnForParent', {
            btnClick: this.btnClick,
            messageTask: this.messageTask,
            numberTask: this.numberTask
        });
      }

  }

}
</script>

<style lang="sass">
    
    .block
        border-radius: 5px

    p 
        color: white 

</style>