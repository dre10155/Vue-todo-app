<template>
  <div>
    <h1>To Do  List App</h1>
    <div class="form-wrapper">
       <form @submit.prevent="submit">
      <label for="item" >Type to do item</label>
      <br>
      <input type="text" v-model="item">
      <br>
      <button type="submit" @click="addListItem">Add Item</button>
    </form>
    </div>
   <ul>
     <li v-for="(todo, index) in litsArray" :key="todo.id" @click="isCompleted(todo)" :class="{completed: todo.done}">
      {{todo.item}}
      <button type="submit" @click="removeItem(index)">Remove item</button>
     </li>
   </ul>
  </div>
 
</template>

<script>
import {ref} from 'vue'

export default {

  setup(){
    const item = ref('')
    const litsArray = ref([])
  

    const addListItem = ()=>{
      
      litsArray.value.push({
        id:Math.random(100*10),
        item:item.value, 
        done:false
      })
      item.value = ""
    
    }
    const isCompleted = (todo) =>{
      return todo.done = !todo.done
    }

    const removeItem = (index) => {
      return litsArray.value.splice(index,1)
    }

    // Me
    return {
      item,
      litsArray,
      addListItem,
      isCompleted,
      removeItem
    }

  }
  
}
</script>

<style>
h1 {
  text-align: center;
}
.form-wrapper {
  display: flex;
  justify-content: center;
}
.completed {
  text-decoration:line-through;
}
</style>
