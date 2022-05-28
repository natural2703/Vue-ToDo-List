<template>
    <div class="deleteModal">
        <h3>Are you sure</h3>
        <button @click="setShowDeleteModal(false,true)" class="warningBtn">Yes</button>
        <button @click="setShowDeleteModal(false)" class="warningBtn">no</button>
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
    .deleteModal{
        background-color: red;
        position:fixed;
        left:50%;
        top:50%;
        width:200px;
        height: 150px;
        margin-left: -100px;
        margin-top: -75px;
        display:flex;
        flex-direction: column;
        justify-content: space-around;
        background-color: #bbb;
    }
    .warningBtn{
        border:none;
        width:80%;
        align-self: center;
        cursor:pointer;
        background-color: #ddd;
    }
    .warningBtn:hover{
         background-color: #aaa;
         transition-duration: 500ms;
    }
</style>