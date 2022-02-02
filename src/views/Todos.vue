<template>
  <div>
    <router-link to="/">Home</router-link>
    <h2>Список дел</h2>
    <FormAddTodo 
      @add-todo="addTodo" 
    />
    <select class="select" v-model="filter">
      <option value="all">Все</option>
      <option value="completed">Выполненные</option>
      <option value="not-completed">Не выполненные</option>
    </select>
    <Loader v-if="loading"/>
    <TodoList 
      v-else-if="filteredTodos.length"
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
    />
    <p v-else>
      Нет дел
    </p>
  </div>  
</template>

<script>
import TodoList from '../components/TodoList.vue';
import FormAddTodo from '../components/FormAddTodo.vue'
import Loader from '../components/Loader.vue'

export default {
  name: 'App',
  data() {
    return {
      todos: [],
      loading: true,
      filter: 'all',
    };
  },
  components: {
    FormAddTodo,
    TodoList,
    Loader
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(response => response.json())
      .then(json => {
        setTimeout(() => {
          this.todos = json;
          this.loading = false; 
        }, 2000);
      });
  },

  // watch: {
  //   filter(value) {
  //     console.log(value);
  //   }
  // },

  computed: {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos;
      };
      if (this.filter === 'completed') {
        return this.todos.filter(todo => todo.completed);
      }
      if (this.filter === 'not-completed') {
        return this.todos.filter(todo => !todo.completed);
      }
      
    }
  },

  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(newTodo) {
      this.todos.push(newTodo);
    }
  }
}
</script>