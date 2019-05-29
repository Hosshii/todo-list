<template>
  <div>
    <div>TodoList</div>
    <div v-for="task in tasks" :key="task.doTask">
      <div class="name">タスク: {{task.soTask}}</div>
    </div>
    <div>
      <label for>
        タスク
        <input  v-model="newTaskName">
      </label>
      <button @click="addTask">add</button>
    </div>
  </div>
</template>

<script>
export default {
    name: "TodoList",
    data(){
        //let tasks = new Array();
        return {
            newTaskName: "",
            isTaskDone:false,
        };
    },
    methods: {
        addTask() {
            if(this.newTaskName!==""){
                //this.tasks.push({doTask: this.newTaskName, taskFinish: false})
                this.newTaskName=""
                //console.log(this.tasks);
            }
        }
    }
};
</script>

<style >
</style>