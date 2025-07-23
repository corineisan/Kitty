<script setup>
import { RouterLink, RouterView } from 'vue-router';
import ToDoList from "./components/ToDoList.vue"
import { ref } from 'vue';

const todos = ref([
  {title: 'Lorem Ipsum 1', isDone: false},
  {title: 'Lorem Ipsum 2', isDone: false},
  {title: 'Lorem Ipsum 3', isDone: false},
]);

const markTodoAsComplete = (index) => {
  console.log(index)
  todos.value[index].isDone = !todos.value[index].isDone
}

const createTodoHeadler = () => {
const todoTitle = prompt('Enter todo title')

todos.value.push({
  title:  todoTitle,
  isDone: false
});
}

const deleteTodoHandler = (index) => {
  todos.value.splice(index, 1);
}
</script>

<template>
  <div id="todo-page">
    <div id="todo">
    <header>
        GGIT ToDo
    </header>
    <ToDoList :todos="todos" @complete-todo="markTodoAsComplete" @delete-todo="deleteTodoHandler"/>


    <button @click="createTodoHeadler">+ New Task</button>
  </div>
</div> 
</template>

<style scoped>

header {
  background-color: hotpink;
  color: rgb(250, 250, 247);
  padding: 24px;
  font-weight: 600;
}
#todo {
  width: 100%;
  max-width: 250px;
}

#todo-page {
  background-color: powderblue;
  min-height: 100vh;
  min-width: 100vw;
  overflow: hidden;

  display: flex;
  align-items: center;
  justify-content: center;
}

button{
  color: white;
  background-color: hotpink;
  padding: 12px;
  font-size: 18px;
  border: none;
  border-radius: 50px;
  margin:auto;
  margin-top: -22px;
  display: block;
}
</style>
