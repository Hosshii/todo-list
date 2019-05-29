<template>
    <div>
        TodoList
    </div>
    <div v-for="task in tasks" :key="task.name">
        <div class="name">タスク: {{ task.doTask }}</div>
        <div class="price">{{ task.isTaskDone }} 円</div>
        <div v-if="item.price >= 10000">高額商品</div>
    </div>

</template>

<script>
export default {
    name: "ItemList",
    data(){
        return {
            newTaskName: "",
            isTaskDone:false,
            tasks:[
                {doTask:newTaskName,isDone:isTaskDone}
            ]
        }
    }
};
</script>

<style >
    
</style>