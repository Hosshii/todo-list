<template>
  <div>
    <div><h1>TodoList</h1></div>
    <div v-for="task in tasks" :key="task.doTask" >
      
    </div>
    <div>
      <label for>
        タスク
        <input  v-model="newTaskName">
      </label>
      <button @click="addTask">add</button>
    </div>
    <div class="task-list">
        <div class="done">
            <h2>完了</h2>
            <div v-for="(task,a) in tasks" :key="task.doTask" v-if="task.taskFinish">
                <div class="name">タスク: {{task.doTask}} </div>
                <button @click="task.taskFinish= false">未完へ</button>
                <button @click="deleteTask(a)" >削除</button>
            </div>
        </div>

        <div class="not-done">
            <h2>未完</h2>
            <div v-for="(task,a) in tasks" :key="task.doTask" v-if="!task.taskFinish">
                <div class="name">タスク:{{task.doTask}}</div>
                 <button @click="task.taskFinish = true">完了！</button>
                 <button @click="deleteTask(a)" >削除</button>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
    name: "TodoList",
    data(){
        let list = new Array();
        const axious = require('axios');
        const baseUrl="http://naro-todo-server.to-hutohu.trap.show/"
        const usrId="hosshii"
        return {
            newTaskName: "",
            isTaskDone:false,
            tasks:list,
            item:{doTask: this.newTaskName, taskFinish: false}
        };
    },
    methods: {
        addTask() {
            if(this.newTaskName!==""){
                this.tasks.push(this.item)
                this.newTaskName=""
                //console.log(this.tasks);
                axios.post(this.baseUrl+this.usrId, this.item)
            }
        },
        deleteTask(arrayIndex) {
            this.tasks.splice(arrayIndex,1)
            //console.log(arrayIndex)

        }
    }
};

</script>

<style >
</style>