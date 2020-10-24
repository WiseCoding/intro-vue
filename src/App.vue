<template>
  <div class="relative flex flex-col h-full text-center">
    <Header />
    <div className="flex-grow container mx-auto m-6">
      <div className="mx-3">
        <AddTodo />
        <TodoList />
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

  export default {
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
    methods: {},
  };
</script>

<style></style>
