<template>
<div class="container">
  <HelloWorld msg="Welcome to my first Vue app - todo list"/>
  <FilterForm :searchTaskName="searchTaskName" :searchHandle="searchHandle"/>
  <button @click="resetFilter">resetuj filtrowanie</button>
  <button @click="saveDataToStorage">zapisz</button>
  <button @click="loadDataFromStorage">wczytaj</button>
   <form>
    <div>
      <input type='text' placeholder="Write task" v-model="tmpTaskName"/>
    </div>
    <div>
      <input type='submit' @click="addTask" value="add Task">
    </div>
  </form>
  <TaskContainer :rawTask="rawTask"/>
  
  <EditModal v-show="showModal" :task="tasksToShow" :showEditModal="showEditModal" :editSingleTask="editSingleTask"/>
  <WarningModal v-show="showDeleteModal" :setShowDeleteModal='setShowDeleteModal'/>
</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
//import SingleTask from './components/SingleTask.vue'
import EditModal from './components/EditModal.vue'
import FilterForm from './components/FilterForm.vue'
import WarningModal from './components/WarningModal.vue'
import TaskContainer from './components/TaskContainer';
export default {
  name: 'App',
  components: {
    HelloWorld,
   // SingleTask,
    EditModal,
    FilterForm,
    WarningModal,
    TaskContainer
  },
  data(){
    return{
      rawTask:[
        {id:1,name:"first task",done:false},
        {id:2,name:"second task",done:false},
        {id:3,name:"third task",done:false}
      ],
      tasks:[
        {id:1,name:"first task",done:false},
        {id:2,name:"second task",done:false},
        {id:3,name:"third task",done:false}
      ],
      tmpTaskName:"",
      counter:3,
      showModal:false,
      tasksToShow:null,
      searchTaskName:"",
      showDeleteModal:false,
      idToDelete:null
    }
  },
  watch:{},
  methods:{
    setIdToDelete(id){
      this.idToDelete = id;
    },
    setShowDeleteModal(show,decision){
      if(decision){
        //this.callback = callback();
        //callback();
        console.log('delete')
        this.removeTask(this.idToDelete)
      }
      this.showDeleteModal = show;
    },
    setTaskToShow(task){
      console.log(task)
      this.task.tasksToShow = task;
    },
    addTask(e){
      e.preventDefault()
      //console.log(this.tmpTaskName.length)
      if(this.tmpTaskName.length>0){
        this.counter++
        const newTask = {id:this.counter,name:this.tmpTaskName,done:false}
        this.tasks.push(newTask)
        this.rawTask.push(newTask)
        this.tmpTaskName = ""
      }
    },
    removeTask(index){
      console.log(`delete task at ${index}`)
      //console.log(this.tasks[1])

      this.tasks = this.tasks.filter(item=>item.id!==index)
      this.rawTask = this.rawTask.filter(item=>item.id!==index)
    },
    changeStatus(index,status){
      const i = this.tasks.findIndex(item=>item.id==index)
      this.tasks[i].done = status
      this.rawTask[i].done = status
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
      console.log(index);
      this.tasks[index] = task
      this.rawTask[index] = task
    },
    searchHandle(tmpName, tmpStatus){
      this.rawTask = this.tasks.filter(item=>item.name.includes(tmpName));
      this.rawTask = this.rawTask.filter(item=>item.done === tmpStatus);
      console.log(this.rawTask);
    },
    resetFilter(){
      this.rawTask = this.tasks;
    },
    saveDataToStorage(){
      localStorage.setItem('tasks',JSON.stringify(this.tasks))
    },
    loadDataFromStorage(){ 
      const data = localStorage.getItem('tasks')
      console.log(JSON.parse(data))
      this.tasks = JSON.parse(data)
      this.rawTask = JSON.parse(data)
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
