<template>
    <div>
        <p>{{task.name}}</p>
        <p>{{task.id}}</p>
        <button @click="removeTask(task.id)">delete task</button>
    </div>
</template>

<script>
    export default{
        name:'SingleTask',
        props:{
            task:Object,
            removeTask:Function
        },
        methods:{
            
        }
    }
</script>
