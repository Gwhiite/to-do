<template>
  <div>
    <div class="todo-container" v-if="afazer.length > 0">
      <div class="todo" v-for="(todo, index) in afazer" :key="index">
        <p>{{ todo }}</p>
        <span class="remove" @click="removeTodo(index)">remove</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["afazer"],
  methods: {
    removeTodo(todo) {
      this.$emit("remove-todo", todo);
    },
  },
};
</script>

<style scoped>
.todo-container {
  display: flex;
  flex-direction: column;
  margin-top: 20px;
  gap: 20px;
}

.todo {
  border: 2px solid #42b883;
  padding: 10px 20px;
  max-width: 400px;
  min-width: 400px;
  font-size: 1rem;
  border-radius: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.remove {
  cursor: pointer;
  color: red;
}
</style>
