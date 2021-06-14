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
  background: linear-gradient(0deg, rgba(2,0,36,1) 0%, rgba(30,75,81,1) 33%, rgba(44,111,103,1) 49%, rgba(64,123,117,1) 55%, rgba(90,140,135,1) 65%, rgba(213,216,220,1) 100%);
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
