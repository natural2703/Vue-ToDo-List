<template>
    <div>
        <ul class="taskContainer">
        <SingleTask v-for="task in rawTask" :key="task.id" :task="task" :removeTask="removeTask" 
        :changeStatus="changeStatus" :showEditModal="showEditModal" :setTaskToShow="setTaskToShow" 
        :setShowDeleteModal='setShowDeleteModal' :setIdToDelete="setIdToDelete" />
    </ul>
    </div>
</template>

<script>
import SingleTask from "./SingleTask.vue";


export default {
    name:"TaskContainger",
    components:{
        SingleTask
    },
    props:{
        rawTask:Array
    },
    methods:{

    }
}
</script>