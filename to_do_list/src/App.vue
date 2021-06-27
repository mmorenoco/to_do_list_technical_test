<template>
  <div id="app">
    <div class="inputData">
      <AddBar @addTask="addTaskToList"></AddBar>
    </div>
    <div class="showData">  
      <ToDoList :toDoList="toDoList" @deleteCompleted="deleteCompleted"></ToDoList>
    </div>
  </div>
</template>

<script>
import AddBar from './components/AddBar.vue'
import ToDoList from './components/ToDoList.vue'

export default {
  name: 'App',
  components: {
    AddBar,
    ToDoList
  },
  data() {
    return {
      toDoList: []
    }
  },
  methods: {
    addTaskToList(task) {
      console.log(task, 'test')
        this.toDoList.push(task)
        console.log(this.toDoList)
    },
    deleteCompleted() {
      let completed = this.toDoList.filter(element =>  {return element.completed === false})
      console.log(completed)
      this.toDoList = completed;
    }
  }
}
</script>

<style>
  html {
    background-image: radial-gradient(circle, #488ed4, #3b6cad, #2d4d88, #1e2f63, #0d1440);
    box-sizing: border-box;
    font-size: large;
  }

#app {
  align-items: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
}

</style>
