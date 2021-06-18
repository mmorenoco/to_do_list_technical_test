<template>
  <div id="app">
    <AddBar @addTask="addTaskToList"></AddBar>
    <ToDoList :toDoList="toDoList"></ToDoList>
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
    }
  }
}
</script>

<style>
  html {
    box-sizing: border-box;
    background-image: radial-gradient(circle, #488ed4, #3b6cad, #2d4d88, #1e2f63, #0d1440);
    font-size: large;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  align-items: center;
}

</style>
