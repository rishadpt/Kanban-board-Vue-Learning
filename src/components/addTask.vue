<template>
<div class="add_task_container">
    <form @submit="onSubmit" >
<input type="text" v-model="title" placeholder="Title"/> 
<input type="text" v-model="description" placeholder="Description" />
<button  >Add Task</button>
 </form>
</div>
</template>

<script>
export default {
    name: "addTask",
    data () {
        return{
            title: "",
            description: ""
        }
    },
    methods:{
        onSubmit(e){
            e.preventDefault();

            if(!this.title){
                alert("Please add a title")
            }
            else if(!this.description){
                alert("Please add a description")
            }
            
            const newTask = {
                id : Math.floor(Math.random() * 100000),
                title:this.title,
                description:this.description,
            }
            console.log(newTask)
            this.$emit("add-task", newTask)
    
            this.title='',
            this.description=''
        },

    }
}
</script>

<style lang="scss" scoped>
.add_task_container{
    margin-top:4rem;
}
form{
      display: flex;
  flex-direction: column;
  padding:0.5rem;
  input,button{
      padding:0.5rem;

      
      margin-bottom:0.5rem;
  }
}
</style>