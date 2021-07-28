<template>
    <div id="todo-table">
        <todo-form @add:todo="addtodo" />
        <ul>
            <li class="item" v-for="todo in todos" :key="todo.id">
              <span class="name">{{ todo.name }}</span>
              <div class="buttons">
                <button v-if="todo.completed" :style="dynamicStyle" @click="toggleComplete(todo)">✓</button>
                <button v-if="!todo.completed" :style="dynamicStyle2" @click="toggleComplete(todo)">✓</button>
                <button @click="removetodo(todo.id)">X</button>
              </div>
            </li>
        </ul>
    </div>
</template>

<script>
import TodoForm from './TodoForm.vue';

export default {
    name: 'todo-table',
    props: {
        todos: Array,
    },
    components: {
        TodoForm
    },
    computed: {
      dynamicStyle(){
        let check="blue";
        if(this.completed){
          check="green";
        }
        else{
          check="blue";
        }
        return {
          "background-color": check,  
        }
      },
      dynamicStyle2(){
        let check="green";
        if(this.completed){
          check="blue";
        }
        else{
          check="green";
        }
        return {
          "background-color": check,  
        }
      }     
    },
    methods: {
        addtodo(todo) {
            const lastId =
            this.todos.length > 0
                ? this.todos[this.todos.length - 1].id
                : 0;
            const id = lastId + 1;
            const newtodo = { ...todo, id };
            console.log(newtodo);
            this.todos = [...this.todos, newtodo];
        },
        toggleComplete: function(todo){
            todo.completed = !todo.completed;
            dynamicStyle();
        },
        removetodo: function(id){
          this.todos = this.todos.filter(
            todo => todo.id !== id
          )
        }
    }
}
</script>

<style scoped>
.item{
  margin-top: 25px;
}

.buttons{
  float: right;
}
.name{
  display: inline-block;
}
.ok{
  background-color: red;
}
</style>