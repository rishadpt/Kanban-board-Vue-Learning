<template>
  <div class="kanban_container">
    <BoardBox  :action="addTodo" :data="todo" name="To do" />
    <BoardBox  :action="addProgress" :data="onprogress" name="OnProgress" />
    <BoardBox  :action="addCompleted" :data="completed"  name="OnCompleted" />
  </div>
</template>

<script>
import BoardBox from './components/boardContainer.vue'
export default {
  name: 'App',
  components: {
    BoardBox
  },
  data() {
    return {
      todo: [],
      onprogress: [],
      completed: [],
     
    }
  },
  created() {
    this.todo = [
      {
        id: 1,

        title: 'Create a todo list',
        description: 'Create a todo list',
      }
    ],
    this.onprogress = [],
    this.completed = []

  },
  methods: {

    addTodo(task) {

     let dd=  this.todo = [...this.todo, task]
     console.log(dd)
    },
     addProgress(task) {

      this.onprogress = [...this.onprogress, task]
    },
     addCompleted(task) { 
     let ss = this.completed = [...this.completed, task] 
 
    },
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

.kanban_container {
  display: flex;
  gap: 1rem;
  justify-content: center;
}
</style>
