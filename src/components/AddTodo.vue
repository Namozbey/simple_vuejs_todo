<template>
  <form @submit="handleSubmit">
    <input type="text" name="title" v-model="title" placeholder="Enter todo title...">
    <button type="submit" class="btn" >Add</button>
  </form>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    }
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault()
      this.$emit('add-item', this.title)
      this.title = ""
      // console.log(this.title )
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>