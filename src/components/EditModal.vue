<template>
    <div class="modal">
        <form>
            <div><p>X</p></div>
            <div>
                <label>name</label>
                <input type="text"/>
            </div>
            <div>
                <label>done</label>
                <input type="checkbox"/>
            </div>
            <div>
                <input type="submit"/>
            </div>
        </form>
    </div>
</template>
<script>
export default{
    name:"EditModal",
    props:{
        task:Object,
        showEditModal:Function
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
</style>