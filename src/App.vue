<script setup>
import { ref, onMounted, watch } from 'vue';

import BaseLayout from './components/BaseLayout.vue';
import TitleHeader from './components/TitleHeader.vue';
import ListRender from './components/ListRender.vue';
import FooterContainer from './components/FooterContainer.vue';
import FormContainer from './components/FormContainer.vue';

const todos = ref([]);

const deleteTodo = (idToDelete) => {
  todos.value = todos.value.filter(({ id }) => id !== idToDelete);
};

watch(
  todos,
  (newValue) => {
    localStorage.setItem('datas', JSON.stringify(newValue));
  },
  { deep: true }
);

onMounted(() => {
  todos.value = JSON.parse(localStorage.getItem('datas')) || [];
});
</script>

/* Todo app */
<template>
  <BaseLayout>
    <template #header>
      <TitleHeader
        titleDefault="Ajouter un Titre..."
        sub-title="Une Todo liste fait avec VueJs utilisant le localStorage pour le stockage de données"
      />
    </template>
    <template #default>
      <FormContainer :datas="todos" />
      <ListRender :datas="todos" :delete-data="deleteTodo" />
    </template>
    <template #footer>
      <FooterContainer />
    </template>
  </BaseLayout>
</template>

<style scoped></style>
