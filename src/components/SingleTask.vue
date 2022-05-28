<template>
    <li class="singleItem">
        <p>{{task.name}}</p>
        <p>{{task.id}}</p>
        <p>{{task.done}}</p>
        <p class="delBtn" @click="removeTask(task.id)">X</p>
        <button @click="handleDelete">delete task</button>
        <button @click="changeStatus(task.id,!task.done)">set done</button>
         <button @click="handleModal">edit</button>
        
    </li>
</template>

<script>
    export default{
        name:'SingleTask',
        data(){
           return{ 
               modalVisible:false
            }
        },
        props:{
            task:Object,
            removeTask:Function,
            changeStatus:Function,
            showEditModal:Function,
            setShowDeleteModal:Function,
            setIdToDelete:Function
        },
        methods:{
            // showEditModal(show){
            //     console.log('works' + show)
            //     this.modalVisible = !this.modalVisible
            // }
            handleModal(){
                this.showEditModal(true,this.task)
                
            },
            handleDelete(){
                this.setShowDeleteModal(true);
                this.setIdToDelete(this.task.id)
                //this.removeTask(this.task.id);
            }
        }
    }
</script>
<style>
.singleItem{
    display:block;
    padding: 1em;
    margin: 0.5em;
    display:flex;
    flex-direction: column;
    border-radius: 10px;
    background-color: #eee;
    box-shadow: 1px 1px #eee;
}
.delBtn{
    position: absolute;
    cursor:pointer;
}
</style>
