<template>
  <div id="app">
    <MyHeader :addTodo="addTodo" />
    <MyList :todos="todos" :checkTodo="checkTodo" :deleteTodo="deleteTodo" />
    <MyFooter :todos="todos" :checkAllTodo="checkAllTodo" :clearAllTodo="clearAllTodo" />
  </div>
</template>

<script>
import MyFooter from "./components/MyFooter.vue";
import MyHeader from "./components/MyHeader.vue";
import MyList from "./components/MyList.vue";

export default {
  name: "App",
  components: {
    MyFooter,
    MyHeader,
    MyList,
  },
  data() {
    return {
      todos: JSON.parse(localStorage.getItem('todos')) || []
    }
  },
  methods: {
    addTodo(todoObj) {
      this.todos.unshift(todoObj)


    },
    checkTodo(id) {
      this.todos.forEach((todo) => {
        if (todo.id === id) todo.done = !todo.done
      })
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => {
        return todo.id !== id
      })
    },
    checkAllTodo(done) {
      this.todos.forEach((todo) => {
        todo.done = done

      })
    },
    clearAllTodo() {
      this.todos = this.todos.filter((todo) => {
        return !todo.done
      })
    }
  },
  watch: {
    todos: {
      deep: true,
      handler(value) {
        localStorage.setItem('todos', JSON.stringify(value))
      }
    }

  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  max-width: 500px;
  min-width: 300px;
  display: flex;
  flex-direction: column;
  margin: 100px auto;
  border: 1px solid #000;
  padding: 8px;
  border-radius: 5px;
}
input[type="checkbox"] {
  cursor: pointer;
}
</style>
