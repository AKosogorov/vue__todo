<template>
  <div>
    <ul class="todoList">
      <TodoItem         
        v-for = '(todo, i) of todos'
        :key = 'todo.id'
        v-bind:todo = 'todo'
        v-bind:index = 'i'
        v-on:remove-todo = 'removeTodo'
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue'
export default {
  props: ['todos'],
  components: {
    TodoItem
  },
  methods: {
    removeTodo(id) {
      this.$emit('remove-todo', id);
    }
  }
}
</script>

<style>
  .todoList {
    list-style: none;
    margin: 0;
    padding: 0;
  }
</style>