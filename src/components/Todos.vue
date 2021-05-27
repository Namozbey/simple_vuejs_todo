<template>
  <div>
    <div :key="todo.id" v-for="todo in obj.todos">
      <TodoItem :todo="todo" v-on:del-todo="deleteItem" />
    </div>
  </div>
</template>

<script>
import TodoItem from "./Todo.item"

export default {
  name: "Todos",
  components: {
    TodoItem
  },
  props: {
    obj: {  type: Object, required: true }
  },
  methods: {
    deleteItem(_id) {
      this.obj.todos = this.obj.todos.filter(({id}) => id !== _id)
    }
  }
}
</script>

<style scoped>

</style>