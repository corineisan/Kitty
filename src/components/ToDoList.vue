<script setup>
import ToDo from './ToDo.vue'

const emit = defineEmits(['complete-todo', 'delete.todo'])
const props = defineProps({
    todos: {
        type: Array,
        default: []
    }
})

const markTodoAsComplete = (index) => {
    emit('complete-todo', index)
}

const deleteTodoHandler = (index) => {
    emit('delete-todo', index)
}
</script>

<template>
    <div id="todos-container">
     <ToDo v-for="(todo, index) in todos" :key="index" :todo="todo"
        @complete-todo="() => markTodoAsComplete(index)"
        @delete-todo="() => deleteTodoHandler(index)" />
    </div>
</template>

<style scoped>
#todos-container{
  background-color: white;
  padding: 24px;
  margin-top: 26px;
}
</style>
