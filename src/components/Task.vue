<template>
  <div @click="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>{{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>



<script>
export default {
  name: 'Tasks',
  props: {
   task: Object,
  }
}
</script>

<style scoped>
.fas {
  color: #e9452f;
  padding: 6px;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid #15c786;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
