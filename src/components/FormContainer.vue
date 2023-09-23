<script setup>
import { ref } from 'vue';

const newItem = ref({ title: '', content: '' });

const props = defineProps(['datas']);

const addItem = (currDatas) => {
  const newId = currDatas.length + 1;
  const title = newItem.value.title || '';
  const content = newItem.value.content || '';

  currDatas.push({
    id: newId,
    title,
    content,
    done: false,
    createdAt: new Date()
  });

  newItem.value.title = '';
  newItem.value.content = '';
};
</script>

<template>
  <form @submit.prevent="addItem(props.datas)">
    <h2>Ajoute des tâches</h2>
    <input v-model="newItem.title" placeholder="titre de la tâche" />
    <textarea v-model="newItem.content" placeholder="description..."></textarea>
    <button type="submit">Ajouter une tâche</button>
  </form>
</template>

<style scoped></style>
