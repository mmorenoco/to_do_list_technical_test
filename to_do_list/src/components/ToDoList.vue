<template>
    <div class="to-do-container">
        <div class="add-bar-container">
            <div class="add-bar">
                <input class="add-bar__input" type="text" name="addToDoTask" id="addToDoTask" v-model="toDo" @keypress.enter="addTask" >
                <button class="add-bar__button" type="text" @click="addTask">Add</button>
            </div>
        </div>
        <div class="to-do">
            <ul class="to-do__list">
                <li class="to-do__list--task" v-for="task in toDoList" :key="task.index">
                    <input type="checkbox" v-model="task.completed">
                    <span :class="{ 'to-do__list--task-completed': task.completed}" >{{ task.toDo }}</span>
                </li>
            </ul>
            <button class="to-do__button" type="submit" @click="deleteCompleted">Delete completed</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ToDoList',
    props: ['toDoList'],
    data() {
        return {
            completed: false,
            toDo: ''
        }
    },
    methods: {
        addTask() {
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
        },
        deleteCompleted(){
            this.$emit('deleteCompleted')
        }
    }
}
</script>

<style scoped> 

    .to-do-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 70%;
    }

    .add-bar-container {
        background: #566573;
         -webkit-box-shadow: 0px 0px 15px 0px rgba(19,141,117,0.5);
        -moz-box-shadow: 0px 0px 15px 0px rgba(19,141,117,0.5);
        box-shadow: 0px 0px 15px 0px rgba(19,141,117,0.5);
        box-sizing: border-box;
        margin-top: 5%;
        margin-bottom: 2%;
        padding: 15px;
        width: 50%;
        border-radius: 5px;
    }

    .add-bar {
        background: #ABB2B9;
        border-radius: 5px;
        display: flex;
        flex-direction: row;
        border-radius: 5px;
    }

    .add-bar__input {
        background: #ABB2B9;
        border: none;
        padding: 15px;
        width: 75%;
        border-radius: 5px;
    }

    .add-bar__input:focus {
        outline: none;
    }

    .add-bar__button  {
        background: #EC7063;
        border: none;
        border-radius: 5px;
        color: white;
        font-weight: bold;
        margin: 15px;
        padding: 10px 30px;
    }

    .add-bar__button:hover {
        cursor: pointer;
        filter: brightness(125%);
        outline: none;
    }

    .to-do {
        background: #566573;
        color: #48C9B0;
         -webkit-box-shadow: 0px 0px 15px 0px rgba(19,141,117,0.5);
        -moz-box-shadow: 0px 0px 15px 0px rgba(19,141,117,0.5);
        box-shadow: 0px 0px 15px 0px rgba(19,141,117,0.5);
        box-sizing: border-box;
        width: 50%;
        border-radius: 5px;
    }

    .to-do__list {
        list-style-type: none;
        padding-inline-end: 40px;
    }

    .to-do__list--task {
        border-bottom: 1px solid #48C9B0;
        padding-top: 10px;
        padding-bottom: 10px;

    }

    .to-do__list--task-completed {
        text-decoration: line-through;
    }

    input {
        margin-right: 20px;
    }

    .to-do__button {
        background: #138D75;
        border: none;
        border-radius: 5px;
        color: white;
        font-weight: bold;
        margin-left: 40px;
        margin-bottom: 20px;
        padding: 15px 25px;
    }

    .to-do__button:hover {
        cursor: pointer;
        filter: brightness(125%);
        outline: none;
    }

    @media only screen and (max-width: 576px){
        .to-do-container {
            width: 100%;
        }

        .to-do {
            min-width: 95%;
            border-radius: 5px;
        }
        
        .add-bar-container {
            border-radius: 5px;
            width: 95%;
        }

        .add-bar {
            width: 100%;
        }
    }
</style>