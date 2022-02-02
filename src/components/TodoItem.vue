<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" v-on:change = "todo.completed = !todo.completed">
      <strong>
        {{index + 1}}
      </strong>
      {{todo.title | uppercase}}
    </span>
    <button class="delete-btn" v-on:click = "$emit('remove-todo', todo.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: Number,
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase();
    }
  }
}
</script>

<style scoped>
  li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    margin-bottom: 1rem;
    padding: .5rem 2rem;
  }

  input {
    margin-right: 1rem;
  }

  .delete-btn {
    background-color: red;
    color: #fff;
    border: none;
    border-radius: 50%;
    font-weight: bold;
    cursor: pointer;
  }

  .delete-btn:hover {
    background-color: rgb(122, 1, 1);
  }

  .done {
    text-decoration: line-through;
  }
</style>