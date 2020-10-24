<template>
  <div
    class="flex flex-row items-center justify-between p-1 my-2 bg-gray-200 rounded-full"
  >
    <div title="Mark as complete!" @click="completeTodo">
      <svg
        class="hover:scale-125 hover:bg-green-500 w-6 h-6 p-1 mx-1 ml-2 transform bg-gray-400 border border-gray-700 rounded-full cursor-pointer"
        fill="currentColor"
        viewBox="0 0 20 20"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          fill-rule="evenodd"
          d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
          clip-rule="evenodd"
        />
      </svg>
    </div>
    <p class="w-full p-2 overflow-y-scroll text-left text-black">
      {{ body }}
    </p>
    <div title="Delete me!" @click="deleteTodo">
      <svg
        class="hover:scale-125 hover:bg-red-500 w-6 h-6 p-1 mx-1 mr-2 transform bg-red-300 border border-gray-700 rounded-full cursor-pointer"
        fill="none"
        stroke="currentColor"
        viewBox="0 0 24 24"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"
        />
      </svg>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      id: { type: String, required: true },
      body: { type: String, required: true },
      completed: { type: Boolean, required: true },
    },
    methods: {
      completeTodo() {
        console.log(this.id);
      },
      deleteTodo() {
        console.log(this.body);
      },
    },
  };
</script>
