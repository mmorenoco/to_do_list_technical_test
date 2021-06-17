<template>
  <div class="topBar">
      <div class="addBar">
          <input type="text" name="addToDoTask" id="addToDoTask" v-model="toDo">
          <button type="submit" @click="addTask">Add</button>
      </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
                checked: false,
                toDo: ''
        }
    },
    methods: {
        addTask() {
            console.log(this.checked, this.toDo)
            const task = {
                checked: this.checked,
                toDo: this.toDo
            }
            if(this.toDo ===''){
                return 
            }
            this.$emit('addTask', task)
            this.resetAddBar()
        },
        resetAddBar() {
            this.checked = false
            this.toDo = ''
        }
    }
}
</script>

<style scoped>
.topBar {
    background: white;
    padding: 15px;
    width: 50%;
    margin-top: 5%;
    margin-bottom: 2%;
    box-sizing: border-box;
    -webkit-box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
    -moz-box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
    box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
}

.addBar {
    background: #EAECEE;
    border-radius: 5px;
}

#addToDoTask {
    border: none;
    background: #EAECEE;
    width: 80%;
    padding: 15px;
}

#addToDoTask:focus {
    outline: none;
}

button  {
    border: none;
    background: #C70039;
    color: white;
    font-weight: bold;
    margin: 15px;
    padding: 10px 15px;
    border-radius: 5px;
}

button:hover {
    outline: none;
    filter: brightness(125%);
    cursor: pointer;
}
</style>