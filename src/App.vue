<template>
  <div id="app">
    <h1>Todo Web App</h1>
    <div class="input-container">
      <input
        @keyup.enter="handleClick"
        type="text"
        placeholder="Digite seu afazer"
        v-model="value" />
      <span @click="handleClick">+</span>
    </div>

    <TodoItem :afazer="todos" @remove-todo="receiveEmit" />
  </div>
</template>

<script>
import TodoItem from "./components/TodoItem.vue";
export default {
  components: { TodoItem },
  name: "App",
  data() {
    return {
      value: "",
      todos: [],
    };
  },
  methods: {
    receiveEmit(todo) {
      this.todos.splice(todo, 1);
      console.log(this.todos);
    },
    handleClick() {
      this.todos.push(this.value);
      this.value = "";
    },
  },
};
</script>

<style>
body {
  background-color: #242424;
  color: white;
}
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  max-width: 700px;
  margin: 0 auto;
  font-family: sans-serif;
}

input {
  min-width: 300px;
  max-width: 300px;
  font-size: 1rem;
  padding: 10px;
  border: 2px solid #42b883;
  border-radius: 8px;
  background-color: #242424;
  color: #42b883;
}

input:focus {
  outline: none;
}

.input-container {
  display: flex;
  align-items: center;
}

.input-container span {
  margin-left: 10px;
  font-size: 2rem;
  color: #42b883;
  cursor: pointer;
}
</style>
