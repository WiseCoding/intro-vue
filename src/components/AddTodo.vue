<template>
  <div class="rounded-xl relative max-w-xl p-2 mx-auto my-8 bg-white shadow-lg">
    <form @submit.prevent="addTodo">
      <input
        name="input"
        type="text"
        placeholder="Add Todo..."
        class="focus:bg-gray-200 hover:bg-gray-200 hover:border-gray-400 w-full p-2 bg-gray-100 border border-gray-100 rounded-lg shadow outline-none"
        required
        ref="userInput"
      />
      <button
        name="submit"
        type="submit"
        title="Add Todo"
        class="bg-gradient-to-r hover:from-blue-600 hover:to-green-600 hover:shadow-lg hover:scale-125 absolute bottom-0 right-0 p-0 mt-4 text-white transform translate-x-1 translate-y-1 bg-gray-800 border border-gray-700 rounded-full cursor-pointer"
        :class="[
          submit ? 'from-blue-600 to-green-600 shadow-lg scale-125' : 'shadow',
        ]"
      >
        <svg
          class="w-6 h-6"
          :class="[submit ? 'animate-spin' : '']"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M12 6v6m0 0v6m0-6h6m-6 0H6"
          ></path>
        </svg>
      </button>
    </form>
  </div>
</template>

<script>
  export default {
    emits: ['add-todo'],
    data() {
      return {
        submit: false,
      };
    },
    methods: {
      addTodo() {
        this.submit = true;
        this.$emit('add-todo', this.$refs.userInput.value);
        this.$refs.userInput.value = '';
        setTimeout(() => {
          this.submit = false;
        }, 400);
      },
    },
  };
</script>

<style scoped></style>
