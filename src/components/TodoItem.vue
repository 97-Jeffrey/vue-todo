<template>
  <div class="todo-item" 
  v-bind:class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" :checked="todo.completed">
      {{todo.title}}
      <button v-if="todo.completed" class="complete-btn">Completed</button>
      <button @click= "$emit('del-todo',todo.id)" class="del">remove </button>
    </p>
  </div>
</template>

<script>
export default {
  name:"TodoItem",
  props:["todo"],
  methods: {
    markComplete(){
       this.todo.completed = !this.todo.completed;
 
    }
  },
}
</script>



<style scoped>

.todo-item{
  background: #f4f4f4;
  padding:10px;
  border-bottom: 1px #ccc dotted;
}
.todo-item:hover{
  background: #a09f9f;
}

.is-complete{
  text-decoration: line-through;
}

.del{
  background: rgb(224, 66, 66);
  color:#fff;
  border:none;
  padding: 5px 9px;
  border-radius: 10px;
  cursor:pointer;
  float:right;
}
.del:hover{
  background: red;
}
.complete-btn{
  background: rgb(3, 167, 3);
  color:#fff;
  border:none;
  border-radius:10px;
  margin-left:40px;
  padding: 4px 8px;

}


</style>