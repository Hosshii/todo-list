<template>
    <div>
        TodoList
    </div>

    <div v-for="item in tasks" : key="item.doTask">

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
                {doTask:newTaskName, isDone:isTaskDone}
            ]
        }
    }
};
</script>

<style >
    
</style>