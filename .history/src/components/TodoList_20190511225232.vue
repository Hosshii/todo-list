<template>
  <div>
    <div>TodoList</div>
    <div v-for="task in tasks" :key="task.doTask">
      <div class="name">タスク: {{task.doTask}}</div>
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

        </div>
        <div class="not-done"></div>
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