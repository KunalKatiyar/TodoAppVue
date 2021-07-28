<template>
  <div id="app" class="small-container">
    <h1>Todos</h1>
    <router-view to="/" v-bind:todos="todos"></router-view>
  </div>
</template>

<script>
  import TodoTable from '@/components/TodoTable.vue'
  import TodoForm from '@/components/TodoForm.vue'
  export default {
    name: 'app',
    components: {
      TodoTable,
      TodoForm
    },
    methods: {
      // async handletodos() {
    	// try{
      //   	const res= await fetch("fetch url");
      //       const data = await res.json();
      //       this.todos = data;
      //   }
      //   catch(error){
      //   	console.error(error);
      //   }
      // },
      // async addTodo(todo) {
      //   try {
      //     const response = await fetch('add url', {
      //       method: 'POST',
      //       body: JSON.stringify(todo),
      //       headers: { 'Content-type': 'application/json; charset=UTF-8' },
      //     })
      //     const data = await response.json()
      //     this.todos = [...this.todos, data]
      //   } catch (error) {
      //     console.error(error)
      //   }
      // },
      // async deleteEmployee(id) {
      //   try {
      //     await fetch('delete url', {
      //       method: "DELETE"
      //     });
      //     this.todos = this.todos.filter(todo => todo.id !== id);
      //   } catch (error) {
      //     console.error(error);
      //   }
      // }
    },
    data() {
      return {
        todos: [
          {
            id: 1,
            name: 'Clean',
            completed: true,
          },
          {
            id: 2,
            name: 'Walk',
            completed: false,
          }
        ],
      }
    },
    mounted(){
      // this.handletodos();
    }
  }
</script>

<style>
  button {
    background: #009435;
    border: 1px solid #009435;
  }

  .small-container {
    max-width: 680px;
  }
</style>