<template>
  <div class="container mx-auto">
    <h1 class="mt-8 text-2xl">Todos</h1>
    <div class="mt-3">
      <div class="grid grid-cols-12 gap-4">
        <div
          class="col-span-6 space-y-4 overflow-y-auto px-1"
          style="height: 500px"
        >
          <div
            v-for="(todo, index) in todos"
            :key="index"
            class="p-8 bg-white shadow-md rounded flex items-center justify-between"
          >
            <div>
              <div>{{ todo.title }}</div>
              <div class="text-gray-500 text-sm">
                {{ todo.createdAt.toString() }}
              </div>
            </div>
            <div class="space-x-2">
              <button
                class="px-1 text-red-600"
                title="Remove todo"
                style="font-size: 26px"
              >
                &times;
              </button>
              <button
                class="px-1 text-green-600"
                title="Mark as complete"
                style="font-size: 20px"
              >
                &check;
              </button>
              <button
                class="px-1 text-yellow-600"
                title="Mark as undone"
                style="font-size: 20px"
              >
                &#8630;
              </button>
            </div>
          </div>
          <div
            v-if="todos.length === 0"
            class="px-8 py-16 bg-white text-gray-700 shadow-md rounded text-sm"
          >
            <p>You don't have tasks todo</p>
          </div>
        </div>
        <div class="col-span-6">
          <div class="p-8 bg-white shadow-md rounded">
            <h2 class="text-xl">Add todo</h2>
            <input
              v-model="inputText"
              @keydown.enter="addTodo()"
              type="text"
              class="p-2 mt-4 border rounded w-full"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// Composition API
import { defineComponent, reactive, ref } from "vue";

export default defineComponent({
  setup() {
    const todos = reactive([]);
    const inputText = ref(""); // it will be stored like: const inputText = {value: ""}

    function addTodo() {
      todos.unshift({
        title: inputText.value,
        createdAt: new Date(),
        done: false,
      });

      inputText.value = "";
    }

    return {
      todos,
      inputText,
      addTodo,
    };

    // In ES6 syntax also possible to use like this:
    // return {
    //   todos,
    // };
  },
});
</script>
