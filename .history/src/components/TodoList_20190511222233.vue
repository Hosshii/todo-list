<template>
  <div>
    <div>TodoList</div>
    <div v-for="task in tasks" :key="task.doTask">
      <div class="name">タスク: {{task.doTask}}</div>
    </div>
  </div>
</template>

<script>
export default {
    name: "ItemList",
    data(){
        let list = new Arry()
        return {
            newTaskName: "",
            isTaskDone:false,
        };
    }
};
</script>

<style >
</style>