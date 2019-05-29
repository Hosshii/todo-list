<template>
    <div>
        TodoList
    </div>
    <div v-for="task in tasks" :key="task.name">
        <div class="item" :class="{over500: task.task>=500}">
        <div class="name">名前: {{ item.name }}</div>
        <div class="price">{{ item.price }} 円</div>
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
                {task:newTaskName,isDone:isTaskDone}
            ]
        }
    }
};
</script>

<style >
    
</style>