<template>
<div>
  <HelloWorld msg="Welcome to my first Vue app - todo list"/>
   <form>
    <input type='text' placeholder="Write task" v-model="tmpTaskName"/>
    <input type='submit' @click="addTask">
  </form>
  <ul v-for="task in tasks" :key="task.id">
      <li>
        <SingleTask :task="task" :removeTask="removeTask"/>
      </li>
  </ul>
</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import SingleTask from './components/SingleTask.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    SingleTask
  },
  data(){
    return{
      tasks:[
        {id:1,name:"first task",done:false},
        {id:2,name:"second task",done:false},
        {id:3,name:"third task",done:false}
      ],
      tmpTaskName:"",
      counter:3
    }
  },
  methods:{
    addTask(e){
      e.preventDefault()
      console.log(this.tmpTaskName)
      this.counter++
      const newTask = {id:this.counter,name:this.tmpTaskName,done:false}
      this.tasks.push(newTask)
      this.tmpTaskName = ""
    },
    removeTask(index){
      console.log(`delete task at ${index}`)
      console.log(this.tasks[1])
      this.tasks = this.tasks.filter(item=>item.id!==index)

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
