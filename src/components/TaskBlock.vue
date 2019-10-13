<template>
  <div 
    class="main col-12 mx-auto d-flex-row mt-5 mb-3"
  >
    <div
        class="info d-flex justify-content-between"
        :style="isBorderBottom ? 'border-bottom: 1px solid white' : 'border-bottom: none'"
    >
        <div
            class="w-50 d-flex justify-content-between ml-2 align-items-center"
        >
            <input 
                type="checkbox"
                v-model="checked" 
            >
            <div
                class="message"  
                :style="checked ? 'text-decoration: line-through' : 'text-decoration: none'"
            > 
                {{ messageTask }}     
            </div>           
        </div>
        <div
            class="w-25 d-flex justify-content-around mb-2 mt-2"    
        >   
            <div    
            >
                <img 
                    title="Change"
                    alt="Exchange icon" 
                    src="../assets/change.png"
                    @click="btnChange"
                >
            </div>
            <div>    
                <img 
                    title="Delete"
                    alt="Trash icon" 
                    src="../assets/delete.png"
                    @click="btnDelete"
                >
            </div>        
        </div>
    </div>
    <div
        class="d-flex justify-content-around align-items-center mt-3 mb-3"
        v-if="isForChangeDiv"
    >
        <input 
            type="text" 
            class="newInputTask form-control w-75" 
            id="taskForm" 
            :placeholder="messageTask"
            maxlength="12" 
            required
        >
        <img 
            title="Apply"
            alt="Apply icon" 
            src="../assets/done.png"
            @click="btnApply"
            width="32px"
            height="32px"
            >

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
  },
  
  data() {
    return {
      btnClick: '',
      checked: false,
      isForChangeDiv: false,
      newInputTask: null,
      isBorderBottom: false
    }
  },
  
  methods: {
      
      btnChange() {
        this.isForChangeDiv = !this.isForChangeDiv;
        this.isBorderBottom = !this.isBorderBottom;
      },

      btnDelete() {
         this.$parent.$emit('clickDelForParent', {
            numberTask: this.numberTask
        });    
      },

      btnApply() {
        this.newInputTask = document.querySelector('.newInputTask');  
        if(this.newInputTask.value) {
            this.$parent.$emit('changeMesForParent', {
            messageTask: this.newInputTask.value,
            numberTask: this.numberTask
        });
        }
        this.isForChangeDiv = false;
        this.isBorderBottom = false;    
      }
  }

}
</script>

<style lang="sass" scoped>
    
    .main
        border-radius: 5px
        border: 2px solid white

    .message 
        width: 105px
        color: white
        text-align: left
        
    img[title="Delete"], img[title="Change"], img[title="Apply"]
        cursor: pointer    

</style>