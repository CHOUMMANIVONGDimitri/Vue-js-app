<script setup>
import { ref, onMounted, watch } from 'vue'

const todos = ref([])
const name = ref('')
const newTodo = ref({ title: '', content: '' })
const isTitleEdit = ref(false)

const addTodo = () => {
  const newId = todos.value.length + 1
  todos.value.push({
    id: newId,
    title: newTodo.value.title,
    content: newTodo.value.content,
    done: false,
    createdAt: new Date()
  })
  newTodo.value.content = ''
  newTodo.value.title = ''
}

const deleteTodo = (idToDelete) => {
  todos.value = todos.value.filter(({ id }) => id !== idToDelete)
}

watch(name, (newName) => {
  localStorage.setItem('title', newName)
})

watch(
  todos,
  (newValue) => {
    localStorage.setItem('datas', JSON.stringify(newValue))
  },
  { deep: true }
)

onMounted(() => {
  name.value = localStorage.getItem('title') || ''
  todos.value = JSON.parse(localStorage.getItem('datas')) || []
})
</script>

/* Todo app */
<template>
  <h1>
    <input v-if="isTitleEdit" v-model="name" placeholder="Titre de la liste" />
    <span v-else>{{ name }}</span>
    <button @click="isTitleEdit = !isTitleEdit">{{ isTitleEdit ? 'save' : 'edit' }}</button>
  </h1>
  <p>liste de mes tâches</p>

  <form @submit.prevent="addTodo">
    <h2>Ajoute des tâches</h2>
    <input v-model="newTodo.title" placeholder="titre de la tâche" />
    <textarea v-model="newTodo.content" placeholder="description..."></textarea>
    <button>Ajouter une tâche</button>
  </form>

  <ul v-if="todos.length > 0">
    <li v-for="todo in todos" :key="todo.id">
      <input type="checkbox" v-model="todo.done" />
      <span :class="{ done: todo.done }">{{ todo.content }}</span>
      <button @click="deleteTodo(todo.id)">Supprimer</button>
    </li>
  </ul>

  <div>
    <h1>test</h1>
    <p>test</p>
  </div>
</template>

<style scoped></style>
