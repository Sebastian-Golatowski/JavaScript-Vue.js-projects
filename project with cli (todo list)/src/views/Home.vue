<script setup>
import Tasks from '../components/Tasks.vue';
import AddTask from '../components/AddTask.vue';
</script>


<template>
    <div v-if="showAddTask">
      <AddTask @add-task="addTask"/>
    </div>
    <Tasks @toggle-reminder ="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
</template>

<script>
export default {
    props:{
        showAddTask: Boolean
    },
    data() {
        return {
            tasks:[]
        }
    },
    methods: {
    addTask(data){
      this.tasks.push(data)
    },
    deleteTask(id){
      if(confirm("Are u sure?")){
        this.tasks = this.tasks.filter((task)=>task.id !==id)
      }
    },
    toggleReminder(id){
      for (let index = 0; index < this.tasks.length; index++) {
        let task = this.tasks[index]
        if (task.id==id)
          task.reminder = !task.reminder
      }

      // this.tasks = this.tasks.map((task)=>task.id == id ? {...task,reminder: !task.reminder} : task)
    },
    
    // async fetchTasks () {
    // const res = await fetch( "http://localhost : 5000/tasks")
    // const data = await res.json()
    // return data
    // }

    // async fetchTask (id) {
    // const res = await fetch ( `http://localhost: 5000/tasks/${id}`)
    // const data = await res.json()
    // return data
    // },

    // async addTask(task) {
    // const res = await fetch('api/tas ks',{
    // method: 'POST',
    // headers:{
    //   'Content-type': 'application/jason'
    // },
    // body: JSON.stringify(task)
    // })
    // const data = await res.json()
    // this.tasks = [...this.tasks, data]
    // },
    },
    created() {
        this.tasks = [
        {
            id:1,
            text:'Task 1',
            day:'March 1st at 2:30 pm',
            reminder:true,
        },
        {
            id:2,
            text:'Task 2 ',
            day:'March 3rd at 2:30 pm',
            reminder:true,
        },
        {
            id:3,
            text:'Task 3',
            day:'March 3rd at 11:30 am',
            reminder:false,
        },
        ]
    },
}
</script>