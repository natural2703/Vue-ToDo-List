<template>
    <form>
        <h1>Edit form</h1>
        <div>
            <label for="searchInput">filtruj</label>
            <div><input type="text" v-model="text" id="searchInput"/></div>
        </div>
    </form>
</template>

<script>

export default{
    name:"FilterForm",
    props:{
        searchHandle:Function
    },
     data(){
        return{
            text:""
        }
    },
    watch:{
        text(){
            //console.log(this.text);
            this.searchHandle(this.text);
        }
    }
}
</script>
