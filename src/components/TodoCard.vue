<template lang="">
  <div class="card">  
    <header> 
      <div>{{moment(new Date()).format('dddd MMMM Do')}}</div> 
      <h1> VueJs Tutorial ToDo List. </h1>
      <div>{{tasks.length}} tâches</div> 

    </header> 

        <NewTodo @sendTask="addTask"></NewTodo>

        <ToDoList :tasks="tasks" @check="checkTask" @remover="removeTask"></ToDoList>
  </div>

</template>

<script>
import moment from 'moment';
import ToDoList from "./TodoList.vue";

import NewTodo from "./NewTodo.vue";

export default {
  name: "TodoCard",

  components: {
        NewTodo,
        ToDoList,
  },
    
  created: function () {
    this.moment = moment;
  },
  data(){
    return{
      tasks : [],
    }
  },
  methods: {
    addTask(task){
      let taskObject = {
        taskName : task,
        checked : false
      }
      this.tasks.push(taskObject)
    },
    checkTask(index){
          if(index.checked == false){
              index.checked = true
          }
          else if(index.checked == true){
              index.checked = false
          }
    },
    removeTask(index){

    const a = this.tasks.indexOf(index);
    this.tasks.splice(a, 1);
  
    }
  },
  
};
</script> 


<style scoped>
header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 40px;
}
h1{
  color: aquamarine;
  font-size: 24px;
}
.card{
  background-color: #fff;
  padding: 20px;
  border-radius: 20px;
}
</style>
