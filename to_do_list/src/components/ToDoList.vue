<template>
  <div class="to-do">
      <ul class="to-do__list">
        <li class="to-do__list--task" v-for="task in toDoList" :key="task.index">
              <input type="checkbox" v-model="task.completed" @click="taskDone">
              <span :class="{ 'to-do__list--task-completed': isActive }" >{{ task.toDo }}</span>
        </li>
      </ul>
      <button class="to-do__button" type="submit" @click="deleteCompleted">Delete completed</button>
  </div>
</template>

<script>

export default {
    name: 'ToDoList',
    props: ['toDoList'],
    data() {
        return {
            isActive: false
        }
    },
    methods: {
        deleteCompleted(){
            this.$emit('deleteCompleted')
        },
        taskDone() {
            this.isActive = true
            console.log(this.toDoList)
        }
    }
}
</script>

<style scoped> 
    .to-do {
        background: #EAECEE;
        color: #769ED4;
         -webkit-box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
        -moz-box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
        box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
        box-sizing: border-box;
        width: 50%;
    }

    .to-do__list {
        list-style-type: none;
        padding-inline-end: 40px;
    }

    .to-do__list--task {
        border-bottom: 1px solid #769ED4;
        margin-bottom: 15px;
    }

    .to-do__list--task-completed {
        text-decoration: line-through;
    }

    input {
        margin-right: 20px;
    }

    .to-do__button {
        background: #FC65BA;
        border: none;
        border-radius: 5px;
        color: white;
        font-weight: bold;
        margin: 15px;
        padding: 15px 25px;
    }

    .to-do__button:hover {
        cursor: pointer;
        filter: brightness(125%);
        outline: none;
    }


    @media only screen and (max-width: 576px){
        .to-do {
            width: 95%;
            border-radius: 5px;
        }
    }
</style>