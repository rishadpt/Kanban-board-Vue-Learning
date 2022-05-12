<template>
    <div id="drag1" draggable="true" @dragstart="whenDrag" class="card_container">
        <div>
<p  >{{title}}</p>
        <small >{{description}}</small>
        </div>
    </div>
</template>

<script>
export default {
  name: 'BoardCard',
  props:['title', 'description','mode','id'],
  methods:{
     
    whenDrag : (e)=>{
    const dd = e.dataTransfer.setData("card", e.target.id)
    },
  
  },

}
</script>

<style lang="scss" scoped>
.card_container {
    width: 100%;
    background:#fff;
    height:7rem;
    display:flex;
    box-shadow: 0 0.4rem #fff;
    flex-direction: column;
    border-radius:0.3rem;
    margin-bottom:1rem;
    cursor:grab;
    justify-content:space-around;
    align-items:center;
}

.line-through{
    text-decoration: line-through;
}


</style>
