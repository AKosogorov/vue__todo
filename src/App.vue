<template>
  <div class="app">
    <h1>Todo App</h1>
    <hr>

    <router-view /> 
  </div>  
</template>

<style>

* {
  box-sizing: border-box;
}

select {
  margin-bottom: 20px;
  height: 30px;
}

.app {
  font-family: sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin: 0 auto;
  max-width: 1100px;
  min-height: 100vh;
  padding: 0 50px;
}

</style>
