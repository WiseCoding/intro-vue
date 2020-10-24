<template>
  <div class="rounded-xl relative max-w-xl p-2 mx-auto my-8 bg-white shadow-lg">
    <form action="">
      <input
        name="input"
        type="text"
        placeholder="Add Todo..."
        class="focus:bg-gray-200 hover:bg-gray-200 hover:border-gray-400 w-full p-2 bg-gray-100 border border-gray-100 rounded-lg shadow outline-none"
        required
      />
      <button
        name="submit"
        type="submit"
        title="Add Todo"
        class="sm:absolute sm:right-0 sm:bottom-0 bg-gradient-to-r hover:from-blue-600 hover:to-green-600 sm:p-0 hover:shadow-lg sm:translate-x-1 sm:translate-y-1 hover:scale-125 p-1 px-10 mt-4 text-white transform bg-gray-800 border border-gray-700 rounded-full shadow cursor-pointer"
      >
        <svg
          class="w-6 h-6"
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
  export default {};
</script>

<style scoped></style>
