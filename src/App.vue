<template>
<div>
  <HelloWorld msg="Welcome to my first Vue app - todo list"/>
   <form>
    <input type='text' placeholder="Write task"/>
    <input type='submit' @click="addTask">
  </form>
  <ul v-for="task in tasks" :key="task.id">
      <li>
        {{task.name}}
      </li>
  </ul>
</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data(){
    return{
      tasks:[
        {id:1,name:"first task",done:false},
        {id:2,name:"second task",done:false},
        {id:3,name:"third task",done:false}
      ]
    }
  },
  methods:{
    addTask(e){
      e.preventDefault()
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
