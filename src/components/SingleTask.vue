<template>
    <li class="singleItem">
        <p>{{task.name}}</p>
        <p>{{task.id}}</p>
        <p>{{task.done}}</p>
        <p class="delBtn" @click="removeTask(task.id)">X</p>
        <button @click="removeTask(task.id)">delete task</button>
        <button @click="changeStatus(task.id,!task.done)">set done</button>
    </li>
</template>

<script>
    export default{
        name:'SingleTask',
        props:{
            task:Object,
            removeTask:Function,
            changeStatus:Function
        },
        methods:{
            tmp(){
                console.log('works')
            }
        }
    }
</script>
<style>
.singleItem{
    background: red;
    display:block;
    padding: 1em;
    margin: 0.5em;
    display:flex;
    flex-direction: column;
}
.delBtn{
    position: absolute;
    cursor:pointer
}
</style>
