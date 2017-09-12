<template>
  <div class="todo">
    <form>
      <input type="text" v-model="newTodo">
      <button v-on:click="addTodo">ADD</button>
    </form>
    <ul>
      <li v-for="todo in todos">
        {{ todo.text }}
        <button v-on:click="deleteTodo(todo)">DELETE</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data() {
    return {
      newTodo: '',
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo === '') {
        return;
      }

      this.todos.push({
        text: this.newTodo,
      });

      this.newTodo = '';
    },
    deleteTodo(todo) {
      const index = this.todos.indexOf(todo);
      this.todos.splice(index, 1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 0 10px;
}
</style>
