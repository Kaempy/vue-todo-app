<template>
  <div class="title">TODOS</div>

  <ul>
    <li v-for="(todo, i) in todos" :key="i" class="todo-item">
      <span class="has-line-through">👉 {{ todo.name }}</span>
      <button class="delete-btn" @click="deleteTodo(todo.id)">
        🗑️ &nbsp;Delete
      </button>
      <button class="complete-btn" @click="updateTodo(todo)">
        ✅ &nbsp;Completed
      </button>
    </li>
  </ul>

  <div class="input-container">
    <input type="text" v-model="todo" />
    <button class="add-btn" @click="addTodo" :disabled="!todo">Add Todo</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      todo: "",
      todos: [
        {
          id: 1,
          name: "Buy Bread",
          isCompleted: false,
        },
      ],
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        id: this.todos.length + 1,
        name: this.todo,
        isCompleted: false,
      });
    },
    removeTodo() {},
    updateTodo(todo) {
      if (!todo.isCompleted) {
        return {
          ...todo,
          isCompleted: !todo.isCompleted,
        };
      }
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
  },
};
</script>

<style>
.title {
  margin: auto;
  margin-bottom: 15px;
  font-size: 18px;
  font-weight: 600;
  color: gray;
  text-align: center;
}

.add-btn {
  margin-left: 5px;
  background-color: rgb(48, 75, 224);
  color: white;
  border: none;
  border-radius: 0.25rem;
  padding: 0.5rem 0.75rem;
  cursor: pointer;
}

.delete-btn {
  margin-right: 5px;
  margin-left: 20px;
  color: white;
  background-color: rgb(211, 105, 105);
  border: none;
  border-radius: 0.25rem;
  padding: 0.5rem 0.75rem;
  cursor: pointer;
}
.complete-btn {
  margin-left: 20px;
  color: white;
  background-color: rgb(61, 149, 140);
  border: none;
  border-radius: 0.25rem;
  padding: 0.5rem 0.75rem;
  cursor: pointer;
}

.input-container {
  margin: 3rem auto;
  text-align: center;
}

.todo-item {
  margin-bottom: 10px;
}

.has-line-through {
  text-decoration: line-through;
}
</style>
