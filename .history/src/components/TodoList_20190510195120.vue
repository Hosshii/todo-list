<template>
    <div>
        TodoList
    </div>
    <div v-for="task in tasks" :key="task.name">
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