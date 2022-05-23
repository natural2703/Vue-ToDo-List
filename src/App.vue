<template>
<div>
  <HelloWorld msg="Welcome to my first Vue app - todo list"/>
   <form>
    <input type='text' placeholder="Write task" v-model="tmpTaskName"/>
    <input type='submit' @click="addTask" value="add Task">
  </form>
  <ul class="taskContainer">
        <SingleTask v-for="task in tasks" :key="task.id" :task="task" :removeTask="removeTask" :changeStatus="changeStatus" :showEditModal="showEditModal" />
  </ul>
  <EditModal v-show="showModal" :task="this.tasks[0]" :showEditModal="showEditModal"/>
</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import SingleTask from './components/SingleTask.vue'
import EditModal from './components/EditModal.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    SingleTask,
    EditModal
  },
  data(){
    return{
      tasks:[
        {id:1,name:"first task",done:false},
        {id:2,name:"second task",done:false},
        {id:3,name:"third task",done:false}
      ],
      tmpTaskName:"",
      counter:3,
      showModal:true,
      tasksToShow:null
    }
  },
  methods:{
    setTaskToShow(){},
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
    },
    changeStatus(index,status){
      const i = this.tasks.findIndex(item=>item.id==index)
      this.tasks[i].done = status
    },
    showEditModal(){
      this.showModal = !this.showModal;
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
.taskContainer{
  list-style-type:none;
  display:grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}

</style>
