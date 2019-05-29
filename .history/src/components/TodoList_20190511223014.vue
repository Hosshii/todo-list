<template>
  <div>
    <div>TodoList</div>
    <div v-for="task in tasks" :key="task.doTask">
      <div class="name">タスク: {{task.doTask}}</div>
    </div>
    <div>
      <label for>
        名前
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
        let list = new Arry()
        return {
            newTaskName: "",
            isTaskDone:false,
        };
    },
    methods: {
        addTask() {
            if(this.newTaskName!==""){
                list.push
            }
        }
    }
};
</script>

<style >
</style>