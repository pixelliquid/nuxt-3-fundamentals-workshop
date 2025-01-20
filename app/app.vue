<script>
import { defineNuxtComponent } from '#app' // helpful when using options API

export default defineNuxtComponent({
  data: () => ({
    todoList: []
  }),
  methods: {
    fetchtodoList() {
      fetch('https://jsonplaceholder.typicode.com/todos/')
        .then(response => response.json())
        .then(json => {
          this.todoList = json
        })
      // same as above
      // .then(response => {
      //   this.todoList = response.json()
      // })
    }
  },
  // computed properties to show amount of data or filter the data in the json
  computed: {
    numberOfTodos() {
      return this.todoList.length
    },
    completedTodos() {
      return this.todoList.filter(todo => todo.completed)
    },
    remainingTodos() {
      return this.todoList.filter(todo => !todo.completed)
    }
  }
})
</script>

<template>
  <h1>To Do List</h1>
  <button @click="fetchtodoList">Fetch Data</button>
  <pre>{{ numberOfTodos }} total todos
  of which are {{ completedTodos.length }} completed and {{ remainingTodos.length }} remaining</pre>
  <ul>
    <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
      <input type="checkbox" :checked="todo.completed">{{ todo.title }}</input>
    </li>
  </ul>
  <pre>{{ todoList }}</pre>
</template>

<style>
  img {
    width: 100%;
  }
  ul {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }
</style>