<template>
  <form class="form" @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button class="add-btn" type="submit">
      Создать дело
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: '',
    }
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          done: false,
        };

        this.$emit('add-todo', newTodo);
        this.title = '';
      }
    }    
  }
}
</script>

<style scoped>

  form {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0 auto;
    height: 100px;
    max-width: 1000px;
  }

  input {
    border-radius: 4px;
    height: 40px;
    width: 70%;
  }

  button {
    border-radius: 4px;
    padding: 7px 20px;
    background-color: green;
    color: #fff;
  };
</style>