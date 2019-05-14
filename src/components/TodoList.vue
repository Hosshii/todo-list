<template>
  <div>
    <div>
      <h1>TodoList</h1>
    </div>
    <div v-for="task in tasks" :key="task.doTask"></div>
    <div>
      <label for>
        タスク
        <input v-model="newTaskName">
      </label>
      <button @click="addTask(baseUrl)">add</button>
    </div>
    <div class="task-list">
      <div class="done">
        <h2>完了</h2>
        <div v-for="(task,a) in tasks" :key="task.id" v-if="task.taskFinish">
          <div class="name">タスク: {{task.doTask}}</div>
          <button @click="task.taskFinish= false">未完へ</button>
          <button @click="deleteTask(a)">削除</button>
        </div>
      </div>

      <div class="not-done">
        <h2>未完</h2>
        <div v-for="(task,a) in tasks" :key="task.id" v-if="!task.taskFinish">
          <div class="name">タスク:{{task.doTask}}</div>
          <button @click="task.taskFinish = true">完了！</button>
          <button @click="deleteTask(a)">削除</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "TodoList",
  data() {
    let list = new Array()
    const axious = require("axios");
    return {
      id: 0,
      newTaskName: "",
      isTaskDone: false,
      tasks: list,
      item: { id: this.id, doTask: this.newTaskName, taskFinish: false },
      baseUrl: "http://naro-todo-server.to-hutohu.trap.show/hosshii/tasks"
    };
  },
  methods: {
    addTask(url) {
      if (this.newTaskName !== "") {
        this.item = { id: this.id, doTask: this.newTaskName, taskFinish: false }
        this.id++;
        this.tasks.push(this.item);
        this.newTaskName = "";
        axios.post(url, this.item);
        this.getTask(this.baseUrl)
      }
    },
    deleteTask(arrayIndex) {
      this.tasks.splice(arrayIndex, 1);
      //console.log(arrayIndex)
      //axios.delete(this.baseUrl+"/"+arrayIndex);
    },
    getTask(url) {
      axios
          .get(url)
          .then((response) => {
            // handle success
            this.tasks = response.data
            console.log(this.tasks[this.tasks.length])
            return response.data
          })
          .catch(function(error) {
            // handle error
            console.log(error);
          })
          .finally(function() {
            // always executed
          });
    }
  },
   mounted() {
      this.$nextTick(this.getTask(this.baseUrl))
    }
};
</script>

<style >
</style>