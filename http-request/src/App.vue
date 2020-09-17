<template>
 <div id="container">
   <div class="row">
     <div class="col-md-8 offset-md-2 text-center">
       <h3 class="mt-5">TodoList | Vue.js</h3>
       <hr>
       <div class="row">
         <div class="col-md-6 offset-md-3 border d-flex flex-row justify-content-between align-items-center pt-2 pb-2">
           <input type="text" v-model="todoText">
           <button @click="addTodo()" class="btn-btn-primary">Ekle</button>
         </div>
         <hr>
       </div>
       <div class="todo-container">
         //container
         <Todo v-for="todo in todoList" :key="todo"/>
       </div>
     </div>
   </div>
   <button @click="fetchData">fetch data</button>
 </div>
</template>

<script>
import Todo from "@/components/Todo"
import axios from "axios"
export default{
components:{
Todo
},
data(){
  return {
    todoText:"",
    todoList:[],
  }
},
methods:{
  addTodo(){
    axios.post("https://vuejs-firebase-c3d4b.firebaseio.com/todoList.json", {text:this.todoText})    
    .then(response=>{
      console.log(response)
    })
    .catch(e=>{
      console.log(e)
    }) 
  },
    fetchData(){
       axios.get("https://vuejs-firebase-c3d4b.firebaseio.com/todoList.json")
       .then(response=>{
         console.log(response.data)
         for (let key in response.data){
           console.log(response.data[key])
         }
       })
       .catch()
    } 
  }
}

</script>

<style>

</style>
