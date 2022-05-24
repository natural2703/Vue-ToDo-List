<template>
    <div class="modal">
        <form>
            <div><p class="closeBtn" @click="showEditModal(false)">X</p></div>
            <div>
                <label>name</label>
                <input type="text" v-model="newName"/>
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
export default{
    name:"EditModal",
    props:{
        task:Object,
        showEditModal:Function
    },
    data(){
        return{
            newName:this.task!=null?this.task.name:""//this.task.name
        }
    },
    methods:{
        log(e){
           e.preventDefault()
            console.log(this.task)
            console.log(this.newName)
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