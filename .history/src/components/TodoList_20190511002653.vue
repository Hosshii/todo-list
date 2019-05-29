<template>
    <div>
        TodoList
    </div>

    <div v-for="task in tasks">

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
            ],
        };
    }
};
</script>

<style >
    
</style>