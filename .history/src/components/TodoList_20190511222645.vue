<template>
  <div>
    <div>TodoList</div>
    <div v-for="task in tasks" :key="task.doTask">
      <div class="name">タスク: {{task.doTask}}</div>
    </div>
    <div>
      <label for>
        名前
        <input type="text" v-model="newItemName">
      </label>
      <label for>
        価格
        <input type="number" v-model="newItemPrice">
      </label>
      <button @click="addItem">add</button>
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
    }
};
</script>

<style >
</style>