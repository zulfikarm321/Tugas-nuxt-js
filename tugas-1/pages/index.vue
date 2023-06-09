<template>
  <div class="container mx-auto flex flex-col gap-5">
    <header class="my-3 max-h-[20vh] relative">
      <div class="flex items-center justify-between">
        <h1 class="text-3xl font-bold">Todo list</h1>
        <button class="text-blue-500 font-semibold" @click="toggleForm">
          Add Task
        </button>
      </div>
      <div
        class="absolute w-full bg-white p-5 mt-5 shadow-md"
        v-show="showForm"
      >
        <form class="flex flex-col gap-2" @submit.prevent="addTodo">
          <input
            type="text"
            placeholder="title"
            class="border-2 rounded-md px-4 py-2 text-lg"
            v-model="inputForm.title"
            required
          />
          <textarea
            placeholder="description"
            class="resize-y border-2 rounded-md px-4 py-2 text-lg"
            v-model="inputForm.description"
            required
          ></textarea>
          <div class="grid grid-cols-2 gap-5">
            <button class="btn-blue" type="submit">save</button>
            <button class="btn" type="button" @click="toggleForm">
              cancel
            </button>
          </div>
        </form>
      </div>
    </header>

    <section class="max-h-[80vh] overflow-y-scroll p-5">
      <ul v-if="todos.length !== 0">
        <li
          v-for="(todo, index) in todos"
          :key="todo.title"
          class="flex gap-4 border-b-2 py-2"
        >
          <input type="checkbox" v-model="todo.isDone" />
          <div>
            <h3
              class="text-lg font-semibold"
              :style="{
                textDecoration: todo.isDone ? 'line-through' : 'none',
              }"
            >
              {{ todo.title }}
            </h3>
            <p class="text-gray-500">{{ todo.description }}</p>
            <button class="text-red-400" @click="deleteTodo(index)">
              Delete
            </button>
          </div>
        </li>
      </ul>
      <ul v-else>
        <p class="text-center text-lg m-10">Belum ada task</p>
      </ul>
    </section>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      showForm: false,
      inputForm: {
        title: '',
        description: '',
        isDone: false,
      },
      todos: [],
    }
  },
  methods: {
    addTodo() {
      this.todos.push(this.inputForm)
      this.resetForm()
      this.toggleForm()
    },
    deleteTodo(index) {
      this.todos.splice(index, 1)
    },
    toggleForm() {
      this.showForm = !this.showForm
    },
    resetForm() {
      this.inputForm = { title: '', description: '', isDone: false }
    },
  },
}
</script>
