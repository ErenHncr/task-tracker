<template>
    <AddTask
      v-show="showAddTask"
      @add-task="addTask" />
    <Tasks 
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask" 
      :tasks="tasks" />
</template>

<script>
import Tasks from '../components/Tasks';
import AddTask from '../components/AddTask';
export default {
  name: 'Home',
  props: {
    showAddTask: Boolean,
  },
  components: {
    Tasks,
    AddTask,  
  },
   data(){
    return {
      tasks: [],
    }
  },
  methods: {
    fetchTasks(){
      let allTasks = JSON.parse(localStorage.getItem('tasks'));
      if(allTasks === null) {
          allTasks = [];
      }      
      return allTasks;      
    },
    addTask(newTask){
      let oldTasks = this.fetchTasks();
      localStorage.setItem('tasks', JSON.stringify([...oldTasks, newTask]));
      this.tasks = [...this.tasks, newTask];
    },
    deleteTask(id){
      if(confirm('Are you sure?')){
        let allTasks = this.fetchTasks();              
        allTasks = allTasks.filter((task)=> task.id !== id);
        localStorage.setItem('tasks', JSON.stringify(allTasks));
      }
    },
    toggleReminder(id){
      const changeReminder = (task)=> task.id === id 
      ? { ...task, reminder: !task.reminder }
      : task;
      let allTasks = this.fetchTasks();   
      allTasks = allTasks.map(changeReminder);
      localStorage.setItem('tasks', JSON.stringify(allTasks));
      this.tasks = allTasks;
    },
  },
  async created(){
    this.tasks = await this.fetchTasks();
  },
}
</script>