<template>
    <div>
        TodoList
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
                {
                    task:newTaskName,isDone:isTaskDone
                }
            ]
        }
    }
};
</script>

<style >
    
</style>