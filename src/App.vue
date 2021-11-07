<template>
  <div class="container">
    <Header
      @toggle-add-task="toggleAddTask" 
      title="Task Tracker"
      :showAddTask="showAddTask" />    
    <router-view :showAddTask="showAddTask" />
    <Footer />
  </div> 
</template>

<script>
import Header from './components/Header';
import Footer from './components/Footer';

export default {
  name: 'App',
  components: {
    Header,
    Footer,
  },
  data(){
    return {
      showAddTask: false,
    }
  },
  methods: {
    toggleAddTask(){
      this.showAddTask = !this.showAddTask;
    }    
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
}
.btn {
  display: inline-block;
  background: #818181 !important;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
  transition: all 0.3s;
  &.red {
    background: #e9452f !important;
  }
  &.green {
    background: #15c786 !important;
  }
  &:focus {
  outline: none;
  }
  &:active {
  transform: scale(0.98);
  }
  &-block {
    display: block;
    width: 100%;
  }
}
</style>