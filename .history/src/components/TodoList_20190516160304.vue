<template>
  <div>
    <div>
      <h1>TodoList</h1>
    </div>

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
        <div v-for="(task,a) in tasks" :key="`${task.id}`" v-if="task.taskFinish">
          <div class="name">タスク: {{task.doTask}}</div>
          <button @click="goUnDone(baseUrl,task.id)">未完へ</button>
          <button @click="deleteTask(a)">削除</button>
        </div>
      </div>

      <div class="not-done">
        <h2>未完</h2>
        <div v-for="(task,a) in tasks" :key="`${task.id}`" v-if="!task.taskFinish">
          <div class="name">タスク:{{task.doTask}}</div>
          <button @click="goDone(baseUrl,task.id)">完了！</button>
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
    let list = new Array();
    const axious = require("axios");
    return {
      id: 0,
      newTaskName: "",
      taskFinish: false,
      tasks: list,
      item: { id: this.id, doTask: this.newTaskName, taskFinish: false },
      baseUrl: "https://to-hutohu.trap.show/naro-todo-server/hosshii/tasks"
    };
  },
  methods: {
    addTask(url) {
      if (this.newTaskName !== "") {
        
        this.item = {
          id: this.id,
          doTask: this.newTaskName,
          taskFinish: false
        };
        var jsontask=JSON.stringify(this.item)  //objectをjsonに
        
        this.tasks.push(this.item);  //objectの格納

        this.newTaskName = "";
        this.id++;
        axios
          .post(url, this.item)
      }
    },
    deleteTask(arrayIndex) {
      this.tasks.splice(arrayIndex, 1);
    },
    getTask(url) {
      axios
        .get(url)
        .then(response => {
          // handle success
          if (response.data.length !== 0) {
            this.tasks = response.data;   //返ってくるのはオブジェクトっぽい
            console.log(response.data[0].id)
            console.log(this.tasks[this.tasks.length - 1].id)
            this.id = this.tasks[this.tasks.length - 1].id+1;
          }
        })
        .catch(function(error) {
          // handle error
          console.log(error);
        })
        .finally(function() {
          // always executed
        });
    },
    goUnDone(url,id){
      this.tasks[id].taskFinish = false
      console.log("a")
      axios.put(`${url}/${id}`,this.tasks[id])
    },
    goDone(url,id){
      this.tasks[id].taskFinish = true
      console.log(`${url}/${id}`)
      console.log(this.tasks[id])
      this.item=this.tasks[id]
      axios.put(`${url}/${id}`,this.tasks[id])
    }
  },
  mounted() {
    this.$nextTick(this.getTask(this.baseUrl));
  },
  computed: {}
};
</script>

<style >
</style>