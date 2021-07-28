<template>
  <div id="todo-form">
    <form @submit.prevent="handleSubmit">
      <label>Todo</label>
      <input v-model="todo.name" type="text" />
      <button>Add Todo</button>
    </form>
  </div>
</template>

<script>
export default {
    name: 'todo-form',
    data() {
      return {
        todo: {
          name: '',
          completed: false,
        },
      }
    },
    methods: {
      handleSubmit() {
        console.log(this.todo);
        this.$emit('add:todo', this.todo);
      },
    },
}
</script>

<style>
    form {
        margin-bottom: 2rem;
    }
</style>