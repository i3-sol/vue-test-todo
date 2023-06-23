<script setup>
import { ref } from 'vue'

let id = 0

const newTodo1 = ref('')
const newTodo2 = ref('')

const todos = ref([])

function handleAdd() {
  todos.value.push({ id: id++, text1: newTodo1.value, text2: newTodo2.value })
  newTodo1.value = ''
  newTodo2.value = ''
}
function handleCancel() {
  newTodo1.value = ''
  newTodo2.value = ''
}

function handleClose() {
  todos.value = [];
}
</script>
<template>
  <div class="container mx-auto my-6">
    <div class="flex flex-wrap mb-6 -mx-3">
      <div class="w-full px-3 mb-6 md:w-1/2 md:mb-0">
        <label class="block mb-2 text-xs font-bold tracking-wide text-gray-700 uppercase" for="grid-first-name">
          Column One
        </label>
        <input v-model="newTodo1"
          class="block w-full px-4 py-3 mb-3 leading-tight border rounded appearance-none border-sky-500 text-gray-700border focus:outline-none focus:bg-white"
          id="grid-first-name" type="text" placeholder="Input Todo1">
      </div>
      <div class="w-full px-3 mb-6 md:w-1/2 md:mb-0">
        <label class="block mb-2 text-xs font-bold tracking-wide text-gray-700 uppercase" for="grid-first-name">
          Column Two
        </label>
        <input v-model="newTodo2"
          class="block w-full px-4 py-3 mb-3 leading-tight border rounded appearance-none border-sky-500 text-gray-700border focus:outline-none focus:bg-white"
          id="grid-first-name" type="text" placeholder="Input Todo2">
      </div>
    </div>
    <div class="flex justify-end">
      <button @click="handleAdd"
        class="flex-shrink-0 px-5 py-2 mx-5 text-white rounded bg-sky-500 hover:bg-teal-700 hover:border-teal-700"
        type="button">
        Save
      </button>
      <button @click="handleCancel"
        class="flex-shrink-0 px-3 py-2 text-white rounded bg-sky-500 hover:bg-teal-700 hover:border-teal-700"
        type="button">
        Cancel
      </button>
    </div>

    <table class="w-full my-6 text-left rounded-lg">
      <thead class="bg-gray-200">
        <tr>
          <th scope="col" class="px-6 py-3">
            Product name
          </th>
          <th scope="col" class="px-6 py-3">
            Color
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="todo in todos" :key="todo.id">
          <td scope="col" class="px-6 py-3">{{ todo.text1 }}</td>
          <td scope="col" class="px-6 py-3">{{ todo.text2 }}</td>
        </tr>
      </tbody>
    </table>
    <div class="flex justify-end">
      <button @click="handleClose"
      class="px-3 py-2 text-white rounded flex0 bg-sky-500 hover:bg-teal-700 hover:border-teal-700"
      type="button">
      Close
    </button>
    </div>
  </div>
</template>