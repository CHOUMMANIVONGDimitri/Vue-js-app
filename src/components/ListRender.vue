<script setup>
const props = defineProps(['datas', 'deleteData']);
</script>

<template>
  <ul v-if="props.datas.length > 0">
    <li v-for="data in props.datas" :key="data.id">
      <h3>
        <input type="checkbox" v-model="data.done" />
        <span :class="{ done: data.done }">{{ data.title }}</span>
        <button @click="deleteData(data.id)">Supprimer</button>
      </h3>
      <p>{{ data.content }}</p>
    </li>
  </ul>
</template>

<style scoped></style>
