<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title"  name="title" placeholder="add a todo...">
      <input type="submit" value="Add" class='btn'>
    </form>
  </div>
</template>

<script>

export default {
  name:"AddTodo",
  data(){
    return {
      title:""
    }
  },
  methods:{
    addTodo(e){
      e.preventDefault();
      const newTodo = {
        title: this.title,
        completed:false
      }
      this.$emit('add-todo', newTodo);
      this.title = '';
      
    }
  }
}
</script>

<style scoped>
 form{
   display:flex;
   margin-bottom: 30px;
   margin-top:30px;
 }
 input[type="text"]{
   flex:10;
   padding:5px;
   border:3px solid rgb(199, 199, 199);
   border-radius: 10px;
   margin-right:20px;
 }
 input[type="text"]:hover{
   border: 3px solid rgb(168, 168, 168);
 }
 input[type="text"]:focus{
   outline:none;
 }

 input[type="submit"]{
   flex:2;
   margin-right:20px;
 }
</style>