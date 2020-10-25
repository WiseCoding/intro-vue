<template>
  <div class="relative flex flex-col h-full text-center">
    <Header />
    <div className="flex-grow container mx-auto m-6">
      <div className="mx-3">
        <AddTodo @add-todo="saveTodo" />
        <TodoList :todos="todos" />
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
  import Header from './components/Header.vue';
  import Footer from './components/Footer.vue';
  import AddTodo from './components/AddTodo.vue';
  import TodoList from './components/TodoList.vue';
  import uniqid from 'uniqid';

  export default {
    created() {
      if (localStorage.getItem('todos') === null) {
        localStorage.setItem('todos', JSON.stringify([]));
      } else {
        this.todos = JSON.parse(localStorage.getItem('todos'));
      }
    },

    components: {
      Header,
      Footer,
      AddTodo,
      TodoList,
    },
    data() {
      return {
        todos: [],
      };
    },

    provide() {
      return {
        deleteTodo: this.deleteTodo,
        completeTodo: this.completeTodo,
      };
    },

    methods: {
      saveTodo(todo) {
        const newTodo = {
          id: uniqid(),
          body: todo,
          completed: false,
        };
        this.todos = [...this.todos, newTodo];
      },
      deleteTodo(id) {
        this.todos = this.todos.filter((todo) => todo.id !== id);
      },
      completeTodo(id) {
        this.todos = this.todos.map((todo) => {
          if (todo.id === id) {
            return { ...todo, completed: !todo.completed };
          }
          return todo;
        });
      },
    },
    watch: {
      todos() {
        localStorage.setItem('todos', JSON.stringify(this.todos));
      },
    },
  };
</script>

<style></style>
