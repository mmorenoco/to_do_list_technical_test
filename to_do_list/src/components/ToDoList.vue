<template>
  <div class="toDoList">
      <ul>
          <li v-for="task in toDoList" :key="task.index"><input type="checkbox" v-model="task.checked">{{ task.toDo }}</li>
      </ul>
      <button type="submit" @click="deleteTask">Delete completed</button>
  </div>
</template>

<script>
export default {
    name: 'ToDoList',
    props: ['toDoList'],
    methods: {
        deleteTask(key){
            console.log(key)
            if(this.task.checked){
                this.$emit('deleteTask', this.task.index)
            }
        }
    }
}
</script>

<style scoped> 
    .toDoList {
            background: #fff;
            width: 50%;
            -webkit-box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
            -moz-box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
            box-shadow: 0px 0px 15px 0px rgba(253,254,254,0.5);
            box-sizing: border-box;
            color: #16A085;
    }

    ul {
        list-style-type: none;
        padding-inline-end: 40px;
    }

    ul li {
        border-bottom: 1px solid #EAECEE;
        margin-bottom: 15px;
    }

    input {
        margin-right: 20px;
    }

    button {
        border: none;
        background: #16A085;
        color: white;
        font-weight: bold;
        margin: 15px;
        padding: 15px 25px;
        border-radius: 5px;
    }

    button:hover {
        outline: none;
        filter: brightness(125%);
        cursor: pointer;
    }
</style>