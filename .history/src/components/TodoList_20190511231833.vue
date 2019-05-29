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
            
            <div class="name" v-bind="task.isTaskDone">タスク: {{task.doTask}}</div>
        </div>
        <div class="not-done">
            <h2>未完</h2>
            <div class="name" v-bind="!task.isTaskDone">タスク: {{task.doTask}}</div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    name: "TodoList",
    data(){
        
        return {
            newTaskName: "",
            isTaskDone:false,
            tasks:[
                {doTask: this.newTaskName, taskFinish: false}
            ]
        };
    },
    methods: {
        addTask() {
            if(this.newTaskName!==""){
                this.tasks.push({doTask: this.newTaskName, taskFinish: false})
                this.newTaskName=""
                //console.log(this.tasks);
            }
        }
    }
};
</script>

<style >
</style>