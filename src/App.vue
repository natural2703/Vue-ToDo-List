<template>
<div class="container">
  <HelloWorld msg="Welcome to my first Vue app - todo list"/>
  <FilterForm :searchTaskName="searchTaskName" :searchHandle="searchHandle"/>
   <form>
    <div>
      <input type='text' placeholder="Write task" v-model="tmpTaskName"/>
    </div>
    <div>
      <input type='submit' @click="addTask" value="add Task">
    </div>
  </form>
  <ul class="taskContainer">
        <SingleTask v-for="task in tasks" :key="task.id" :task="task" :removeTask="removeTask" 
        :changeStatus="changeStatus" :showEditModal="showEditModal" :setTaskToShow="setTaskToShow" />
  </ul>
  <EditModal v-show="showModal" :task="tasksToShow" :showEditModal="showEditModal" :editSingleTask="editSingleTask"/>
</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import SingleTask from './components/SingleTask.vue'
import EditModal from './components/EditModal.vue'
import FilterForm from './components/FilterForm.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    SingleTask,
    EditModal,
    FilterForm
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
      showModal:false,
      tasksToShow:null,
      searchTaskName:""
    }
  },
  methods:{
    setTaskToShow(task){
      console.log(task)
      this.task.tasksToShow = task;
    },
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
    showEditModal(show, chosenTask){
      if(chosenTask){
        this.tasksToShow = chosenTask
      }
      console.log(show)
      this.showModal = show;
    },
    editSingleTask(task){
      console.log(task)
      const index = this.tasks.findIndex(item=>item.id===task.id)
      this.tasks[index] = task
    },
    searchHandle(tmpName){
      console.log(`tmp name: ${tmpName}`)
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
body{
  background-color: #ddd;
}
</style>
