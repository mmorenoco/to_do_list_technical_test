<template>
  <div class="to-do">
      <ul class="to-do__list">
          <li class="to-do__list--task" v-for="task in toDoList" :key="task.index"><input type="checkbox" v-model="task.checked">{{ task.toDo }}</li>
      </ul>
      <button class="to-do__button" type="submit" @click="deleteTask(task)">Delete completed</button>
  </div>
</template>

<script>
export default {
    name: 'ToDoList',
    props: ['toDoList'],
    methods: {
        deleteTask(task){
            console.log(task)
        }
    }
}
</script>

<style scoped> 
    .to-do {
        background: #fff;
        width: 50%;
        -webkit-box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
        -moz-box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
        box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
        box-sizing: border-box;
        color: #16A085;
    }

    /*
    Clase
    Id
    Tipo de elemento
    Si padre, si es par...
    */

    .to-do__list {
        list-style-type: none;
        padding-inline-end: 40px;
    }

    .to-do__list--task {
        border-bottom: 1px solid #EAECEE;
        margin-bottom: 15px;
    }

    input {
        margin-right: 20px;
    }

    .to-do__button {
        border: none;
        background: #FC65BA;
        color: white;
        font-weight: bold;
        margin: 15px;
        padding: 15px 25px;
        border-radius: 5px;
    }

    .to-do__button:hover {
        outline: none;
        filter: brightness(125%);
        cursor: pointer;
    }


    @media only screen and (max-width: 576px){
        .to-do {
            width: 95%;
            border-radius: 5px;
        }
    }
</style>