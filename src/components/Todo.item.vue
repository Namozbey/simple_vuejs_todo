<template>
  <div class="todo-item">
    <p style="cursor: pointer;" :class="{'is-complete':todo.completed}"  v-on:click="markComplate">
      <input type="checkbox" :checked="todo.completed">
      {{todo.title}}
    </p>
    <button class="del" @click="$emit('del-todo', todo.id)">x</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplate() {
      this.todo.completed = !this.todo.completed
      console.log(this.todo);
    }
  }
}
</script>

<style scoped>
  .todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>
