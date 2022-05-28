<template>
    <div class="modal">
        <h3>Are you sure</h3>
        <button @click="setShowDeleteModal(false,true)">Yes</button>
        <button @click="setShowDeleteModal(false)">no</button>
    </div>
</template>
<script>
export default {
    name:"WarningModal",
    props:{
        setShowDeleteModal:Function
    }
}
</script>
<style >
    .modal{
        
        background-color: red;
    }

</style>