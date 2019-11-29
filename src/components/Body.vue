<template>
  <div class="toDoList">
      <h1>To Do List</h1>
    <ol >
        <li class="button" v-for="(task, index) in tasks"  v-bind:key="index">{{task.title}}
            <button>Done</button>
            <button v-on:click="deleteTask">Delete</button>
        </li>
    </ol>
    <div id="submit">
        <input type="text" v-model="inputValue">
        <input type="submit" v-on:click="submit">
    </div>
  </div>
</template>

<script>
import Task from "../models/Task.js"
export default {
    name: 'toDoList',
    data: () => {
         return {
        inputValue:"",
        tasks: []
            
            }
        },
    methods: {
        submit: function (){ 
            let newTask = new Task(this.inputValue, false);
            this.tasks.push(newTask);
            this.clearInputValue();
        },
        clearInputValue: function(){
            this.inputValue = ""
        },
        deleteTask: function(event){
            console.log(event);
        }
    }

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
*{
    margin: 0px;
}
.toDoList{
    display: flex;
    flex-direction: column;
    border: 2px black solid;
    width: 300px;
    height: 400px;
    margin: 200px auto;
    padding: 0 20px;
}
h1{
    text-align: center;

}
.toDoList ol {
text-align:left;
border: 1px solid black;
margin: 0 10px;
margin-bottom: 20px;
height: 250px;
}
.toDoList .submit{
    border: 2px solid black;
}
#submit input:first-of-type{
    margin-left: 20px;
    width: 200px;
}
#submit input:last-of-type{
    margin-left: 10px;
}
button {
    background-color: rgba(127, 191, 63, 0.69);
    border: none;
    color:black;
    padding: 5px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 8px;
    border-radius: 50%;
}
.button button:first-of-type{
    margin-left:50px;
    margin-right: 10px;
    margin-top: 5px;
}

</style>