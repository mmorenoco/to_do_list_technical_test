<template>
  <div class="add-bar-container topBar">
      <div class="add-bar addBar">
          <input class="add-bar__input" type="text" name="addToDoTask" id="addToDoTask" v-model="toDo" @keypress.enter="addTask" >
          <button class="add-bar__button" type="text" @click="addTask">Add</button>
      </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
                completed: false,
                toDo: ''
        }
    },
    methods: {
        addTask() {
            console.log(this.completed, this.toDo)
            const task = {
                completed: this.completed,
                toDo: this.toDo
            }
            if(this.toDo ===''){
                return 
            }
            this.$emit('addTask', task)
            this.resetAddBar()
        },
        resetAddBar() {
            this.completed = false
            this.toDo = ''
        }
    }
}
</script>

<style scoped>

    .add-bar-container {
        background: #EAECEE;
        -webkit-box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
        -moz-box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
        box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
        box-sizing: border-box;
        margin-top: 5%;
        margin-bottom: 2%;
        padding: 15px;
        width: 50%;
    }

    .add-bar {
        background: #fff;
        border-radius: 5px;
    }

    .add-bar__input {
        background: #fff;
        border: none;
        padding: 15px;
        width: 80%;
    }

    .add-bar__input:focus {
        outline: none;
    }

    .add-bar__button  {
        background: #FCC24C;
        border: none;
        border-radius: 5px;
        color: white;
        font-weight: bold;
        margin: 15px;
        padding: 10px 15px;
    }

    .add-bar__button:hover {
        cursor: pointer;
        filter: brightness(125%);
        outline: none;
    }

    @media  only screen and (max-width: 576px) {
        .add-bar-container {
            border-radius: 5px;
            width: 95%;
        }

        .add-bar {
            width: 100%;
        }
    }
</style>