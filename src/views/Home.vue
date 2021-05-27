<template>
  <div class="home">
    <AddTodo v-on:add-item="addTodo" />
    <Todos :obj="obj"  />
  </div>
</template>

<script>
import axios from "axios"
import Todos from "../components/Todos"
import Header from "../components/layout/Header"
import AddTodo from "../components/AddTodo"
import { v4 as uuidv4 } from 'uuid';

export default {
  name: "Home",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      message: "Hello there, I'm Namoz",
      obj: { todos: [] }
    }
  },
  methods: {
    addTodo(title) {
      this.obj.todos = [...this.obj.todos, {id: uuidv4(), title, completed: false}]
      console.log(title)
    },
    // deleteItem(_id) {
    //   this.obj.todos = this.obj.todos.filter(({id}) => id !== _id)
    // }
  },
  created() {
    axios.get("https://jsonplaceholder.typicode.com/todos?_limit=5")
    .then(res => this.obj.todos = res.data)
    .catch(err => console.log(err))
  }
};
</script>
