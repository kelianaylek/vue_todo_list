<template lang="">

    <div class="tasks">
        <div class="task" v-for="task in tasks" :key="task">
           <div>
                <input @click="check(task)" type="checkbox" id="scales" name="scales">
                <p v-bind:class="{ checked: task.checked}">{{ task.taskName }}</p>
            </div>
            <button @click="remover(task)"><i class="fa fa-trash" aria-hidden="true"></i>
</button>
        </div>
    </div>

</template>

<script>


export default {
  name: "ToDoList",
  props: ["tasks"],

  methods: {
      check(index){
            this.$emit('check', index)
      },
        remover(index){
            this.$emit('remover', index)
      }
  }
    
}

</script>
<style scoped>
.task{
    display: flex;
    align-items: center;
    margin-bottom: 20px;
    justify-content: space-between;
}
.checked{
    text-decoration: line-through;
}
.task input{
    margin-right: 10px;
}
.task p{
    margin-right: 10px;
}
.task button{
  background-color: red;
  border: none;
  border-radius: 20px;
  padding: 5px 10px;
  outline: none;
}
.task button i{
color: #fff;
font-size: 18px;
}
.task div{
display: flex;
align-items: center;
}

</style>

