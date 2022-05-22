<template>
    <li class="singleItem" @click="showEditModal(true)">
        <p>{{task.name}}</p>
        <p>{{task.id}}</p>
        <p>{{task.done}}</p>
        <p class="delBtn" @click="removeTask(task.id)">X</p>
        <button @click="removeTask(task.id)">delete task</button>
        <button @click="changeStatus(task.id,!task.done)">set done</button>
        <EditModal v-show="modalVisible" :task="task" :showEditModal="showEditModal"/>
        
    </li>
</template>

<script>
import EditModal from './EditModal.vue'
    export default{
        name:'SingleTask',
        data(){
           return{ 
               modalVisible:false
            }
        },
        components:{
            EditModal
        },
        props:{
            task:Object,
            removeTask:Function,
            changeStatus:Function
        },
        methods:{
            showEditModal(show){
                console.log('works' + show)
                this.modalVisible = !this.modalVisible
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
