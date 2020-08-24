<template>
  <div id="app">
    <h1>To-Do List</h1>
    <to-do-form @todo-added="addToDo"></to-do-form>
    <ul>
      <li v-for="item in ToDoItems" :key="item.id">
        <to-do-item
          :id="item.id"
          :label="item.label"
          :done="item.done"
        ></to-do-item>
      </li>
    </ul>
  </div>
</template>

<script>
import ToDoForm from './components/ToDoForm.vue';
import ToDoItem from './components/ToDoItem.vue';
import uniqueId from 'lodash.uniqueid';

export default {
  name: 'App',
  components: {
    ToDoItem,
    ToDoForm
  },
  methods: {
    addToDo(toDoLabel) {
      this.ToDoItems.push({ id: uniqueId('todo-'), label: toDoLabel, done: false });
    }
  },
  data() {
    return {
      ToDoItems: [
        { id: uniqueId('todo-'), label: 'Learn Vue', done: false },
        { id: uniqueId('todo-'), label: 'Create a Vue project with the CLI', done: true },
        { id: uniqueId('todo-'), label: 'Have fun', done: true },
        { id: uniqueId('todo-'), label: 'Create a to-do list', done: false }        
      ]
    };
  }
};
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
</style>
