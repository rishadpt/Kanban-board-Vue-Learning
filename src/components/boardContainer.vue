<template>
  <div @drop="whenDrop" @dragover="whenDragover" class="board_container">
    <div className="board_head">
      <p>{{ name }}</p>
      <p @click="formOn">add task</p>
    </div>
    <div v-show="showAddTask">
      <AddTask  @add-task="action" />
    </div>

    <div class="board">

      <BoardCard @delete-task="delete" v-for="(item, index) in data" :id="item.id" :title="item.title"
        :description="item.description" />
    </div>

  </div>

</template>

<script>
import BoardCard from './boardCard.vue'
import AddTask from './addTask.vue'
export default {
  name: 'BoardBox',
  props: {
    name: {
      type: String,
    },
    data: {
      type: Array,
    },
    action: {
      type: Function,
    },
  
  },
  data() {
    return {
      showAddTask: false,
    }
  },
  components: {
    BoardCard,
    AddTask
  },

  methods: {

    whenDrop: (e) => {
      e.preventDefault()
      let getParent = (e) => {
        if (e.target) {
          if (e.target.className === 'board') {
            return e.target

          } else {
            return getParent(e.target.parentElement)
          }

        } else {
          if (e.className === 'board_container') {
            return e
          }
          else {
            return getParent(e.parentElement)
          }
        }
      }
      let parent = getParent(e)
      console.log("parent :", parent)
      e.preventDefault()
      var data = e.dataTransfer.getData("card")
      parent.appendChild(document.getElementById(data));
    },
    whenDragover: (e) => {
      e.preventDefault()
    },

    formOn() {
      this.showAddTask = !this.showAddTask

    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.board_container {
  width: 20rem;
  height: 30rem;
  background-color: #cdcdcd;
  display: grid;
  grid-template-areas: "head"
    "body";
  grid-template-rows: 1fr 7fr;
  overflow-y: auto;

}

.board_head {
  grid-area: head;
  position: fixed;
  width: 20rem;
  background-color: #cdcdcd;
  display: flex;
  justify-content: space-around;
  cursor: pointer;
}

.board {
  grid-area: body;
  padding: 0.5rem;
}
</style>
