<template>
  <div id="app">
    <!-- Acuerdate de identar y tabular correctamente -->
    <ToDoList :toDoList="toDoList" @addTask="addTaskToList" @deleteCompleted="deleteCompleted"></ToDoList>
  </div>
</template>

<script>
import ToDoList from './components/ToDoList.vue'

export default {
  name: 'App',
  components: {
    ToDoList
  },
  data() {
    return {
      toDoList: []
    }
  },
  methods: {
    addTaskToList(task) {
        this.toDoList.push(task)
    },
    deleteCompleted() {
      // ¿Por que usamos LET aqui? Solo usamos let si en algún momento vamos a cambiarle el valor, en este caso no es necesario.
      // Si quitamos los { } no hace falta un return, se sobre entiendo que devuelve algo (Lo sobreentiendo JS)
      // Cuando hagamos un === false o === true, MALA SEÑAL, siempre podemos usar ! o !!   
      let completed = this.toDoList.filter(element =>  {return element.completed === false})
      // Mi versión:
      //const completed = this.toDoList.filter(element => !element.completed)
      this.toDoList = completed;
    }
  }
}
</script>

<style>
  html {
    background-image: radial-gradient(circle, #aeb6bf, #8c96a2, #6b7785, #4b5a6a, #2c3e50);
    box-sizing: border-box;
    font-size: large;
  }

  body {
    margin: 0 auto;
  }

  #app {
    color: #2c3e50;
    display: flex;
    flex-direction: column;
    align-items: center;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    height: 100vh;
  }
</style>
