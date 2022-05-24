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
                <input type="checkbox"/>
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
            this.newTask = this.task
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
        }
    }
}
</script>
<style >
.modal{
    position: fixed;
    background: blue;
    width:300px;
    height:200px;
}
.closeBtn{
    cursor:pointer
}
</style>