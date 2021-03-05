<template lang="">
  <div class="addTask"> 
      <input v-model="titleTask" type="text" placeholder="Nouvelle tâche...">
      <button @click="newTask()"><i class="fa fa-plus" aria-hidden="true"></i>

</button>


  </div>
</template>

<script>
export default {
  name: "NewTodo",
  data(){
    return{
      titleTask: "",

    }
  },
  methods: {
    newTask(){
    if(this.titleTask != "") {
          this.$emit('sendTask', this.titleTask )
          this.titleTask = ""
        }
    }
  },
};


</script>
<style scoped>
.addTask{
  margin-bottom: 20px;
}
.addTask button{
  background-color: aquamarine;
  border: none;
  border-radius: 20px;
  padding: 5px 10px;
  outline: none;
}
.addTask button i{
color: #fff;
font-size: 18px;
}
.addTask input{
font-size: 18px;
border: none;
border-bottom: 1px solid aquamarine;
margin-right: 10px;
text-align: center;
padding-bottom: 5px;
outline: none;
}
</style>

