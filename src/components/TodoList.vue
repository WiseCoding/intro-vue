<template>
  <div
    v-if="todos.length > 0"
    class="rounded-xl relative max-w-xl mx-auto my-8 bg-white shadow-lg"
  >
    <div
      class="rounded-t-xl flex flex-row items-center justify-between text-white bg-gray-700"
    >
      <div
        class="hover:text-blue-600 hover:bg-white p-1 m-2 text-white transform bg-gray-900 border border-gray-300 cursor-pointer"
        :class="[filter ? 'bg-green-500 scale-125 rounded-lg' : 'rounded-full']"
        :title="filter ? 'Show Completed' : 'Hide Completed'"
        @click="hideCompleted"
      >
        <svg
          class="w-4 h-4"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2m-6 9l2 2 4-4"
          ></path>
        </svg>
      </div>
      <h2 class="font-mono">TODOS</h2>
      <div
        class="hover:text-blue-600 hover:bg-white p-1 m-2 text-white bg-gray-900 border border-gray-300 rounded-full cursor-pointer"
        :title="reverse ? 'Sort: Latest' : 'Sort: Oldest'"
        @click="reverseOrder"
      >
        <svg
          class="w-4 h-4"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M7 16V4m0 0L3 8m4-4l4 4m6 0v12m0 0l4-4m-4 4l-4-4"
          ></path>
        </svg>
      </div>
    </div>
    <ul class="p-2 m-2" v-if="printTodos.length > 0">
      <Todo
        v-for="todo in printTodos"
        :key="todo.id"
        :id="todo.id"
        :body="todo.body"
        :completed="todo.completed"
      />
    </ul>
    <ul v-else class="py-3">
      Done ✅
    </ul>
  </div>
  <div v-else class="font-mono">Let's do something 😴</div>
</template>

<script>
  import Todo from './Todo.vue';
  export default {
    components: { Todo },
    props: {
      todos: { type: Array, required: true },
    },
    data() {
      return {
        reverse: false,
        filter: false,
        printTodos: this.todos,
      };
    },
    methods: {
      reverseOrder() {
        this.reverse = !this.reverse;
      },
      hideCompleted() {
        this.filter = !this.filter;
      },
      manageTodos() {
        if (this.filter) {
          if (this.reverse) {
            return this.todos
              .slice(0)
              .reverse()
              .filter((todo) => !todo.completed);
          } else {
            return this.todos.filter((todo) => !todo.completed);
          }
        } else {
          if (this.reverse) {
            return this.todos.slice(0).reverse();
          } else {
            return this.todos;
          }
        }
      },
    },
    watch: {
      todos() {
        this.printTodos = this.manageTodos();
        console.log('test');
      },
      reverse() {
        this.printTodos = this.manageTodos();
      },
      filter() {
        this.printTodos = this.manageTodos();
      },
    },
  };
</script>

<style scoped></style>
