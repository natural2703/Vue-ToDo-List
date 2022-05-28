<template>
    <div class="modal" @submit="saveChanges">
        <form>
            <div><p class="closeBtn" @click="showEditModal(false)">X</p></div>
            <div>
                <label>name</label>
                <input type="text" v-model="newTask.name"/>
            </div>
            <div>
                <label>done</label>
                <input type="checkbox" v-model="newTask.done"/>
            </div>
            <div>
                <input type="submit"/>
            </div>
            <button @click.self="log">log taska</button>
        </form>
    </div>
</template>
<script>
//import {watch} from 'vue'
export default{
    name:"EditModal",
    props:{
        task:Object,
        showEditModal:Function,
        editSingleTask:Function
    },
    data(){
        return{
            newTask:{id:null,name:null,done:null}
        }
    },
    watch:{
        task(){
            this.newTask.id = this.task.id
            this.newTask.name = this.task.name
            this.newTask.done = this.task.done
        }
    },
    methods:{
        log(e){
           e.preventDefault()
            console.log(this.task!=null)
            console.log(this.newName)
        },
        saveChanges(e){
            e.preventDefault()
            this.editSingleTask(this.newTask)
            this.showEditModal(false)
            this.newTask={id:null,name:null,done:null}
        }
    }
}
</script>
<style >
.modal{
    position: fixed;
    background: #ddd;
    width: 500px;
    height: 200px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%)
}
.closeBtn{
    cursor:pointer
}
</style>