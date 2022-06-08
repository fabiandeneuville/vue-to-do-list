<template>

    <div>
        <h1>TO DO LIST with VUE.JS 2</h1>
        <form>
            <label for="addTaskInput">New task : </label>
            <input v-model="formData.task" id="addTaskInput" type="text">
            <button v-on:click.prevent="addTask">+</button>
        </form>

        <p class="error-message">{{ errorMessage }}</p>

        <hr>

        <ul class="tasks-list">
            <li v-bind:key="index" v-for="(task, index) in allTasks">
                <task-item
                v-bind:task="task"
                v-bind:id="index"
                v-bind:deleteTask="deleteTask"
                ></task-item>
            </li>
        </ul>
    </div>

</template>

<script>

import TaskItem from './task-item'

export default {
    name:'MainPage',
    data(){
        return {
            formData: {
                task: ''
            },
            allTasks: [],
            errorMessage: ''
        }
    }, 
    components: {
        'task-item':TaskItem
    },
    methods: {
        addTask: function(){
            if(this.formData.task !== ''){
                this.allTasks.push(this.formData.task);
                this.formData.task = '';
                this.errorMessage = '';
                this.toLocalStorage(this.allTasks);
            } else {
                this.errorMessage = "Please be more specific !"
            }
        },
        deleteTask: function(e){
            this.allTasks.splice(e.target.parentNode.id, 1);
            this.toLocalStorage(this.allTasks);
        },
        toLocalStorage: function(tasks){
            localStorage.setItem('allTasks', JSON.stringify(tasks));
        },
        fromLocalStorage: function(){
            this.allTasks = JSON.parse(localStorage.getItem('allTasks'))
        }
    },
    created(){
        this.fromLocalStorage();
    }
}
</script>

<style scoped>

h1 {
    margin-top: 40px;
    text-align: center;
    font-size:20px;
}

form {
    position: relative;
    width: 90%;
    height: 30px;
    max-width: 600px;
    margin:15px auto;
}

label {
    padding: 0 10px;
    display: inline-block;
    width: 100px;
    height: 100%;
}

button {
    position: absolute;
    right:0px;
    width:25px;
    height: 100%;
    font-size: 25px;
    line-height: 25px;
    border: none;
    background: transparent;
    cursor: pointer;
    color: green;
}

input {
    width: calc(100% - (100px + 25px));
    height: 100%;
    padding:10px;
    border: none;
    border-bottom:1px solid #333;
    background: transparent;
}

.error-message {
    text-align: center;
    padding: 10px;
}

.tasks-list {
    list-style-type: none;
    width:90%;
    max-width: 600px;
    margin: 15px auto;
}

</style>