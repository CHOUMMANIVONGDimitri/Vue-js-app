<script setup>
import { ref, watch, onMounted, nextTick } from 'vue';

const name = ref('');
const isTitleEdit = ref(false);
const inputRef = ref(null);

const props = defineProps(['subTitle', 'titleDefault']);

watch(name, (newName) => {
  localStorage.setItem('title', newName);
});

const handleClickEdit = () => {
  isTitleEdit.value = !isTitleEdit.value;

  nextTick(() => {
    if (isTitleEdit.value && inputRef.value) {
      inputRef.value.focus();
      inputRef.value.select();
    }
  });
};

onMounted(() => {
  name.value = localStorage.getItem('title') || props.titleDefault;
});
</script>

<template>
  <h1 class="title-container">
    <input
      ref="inputRef"
      class="title-content-edit"
      v-if="isTitleEdit"
      v-model="name"
      :placeholder="props.titleDefault"
    />
    <span class="title-content" v-else>{{ name || props.titleDefault }}</span>
    <button class="title-btn btn" @click="handleClickEdit">
      {{ isTitleEdit ? 'save' : 'edit' }}
    </button>
  </h1>
  <p class="title-sub">{{ props.subTitle }}</p>
</template>

<style scoped>
[class^='title-content'] {
  color: aliceblue;
  text-align: center;
  justify-content: center;
  font-size: 2rem;
  background-color: transparent;
  border: none;
}

.title-container {
  text-transform: uppercase;
  text-align: center;
  width: 100%;
  height: 2.5rem;
  padding: 2rem;
  border-radius: 0.5rem;
  transition: all 0.5s;
  background-color: rgb(21, 145, 108);
  cursor: default;
  display: flex;
  justify-content: center;
  align-items: center;

  > button {
    color: aliceblue;
    background-color: transparent;
    border: none;
    cursor: pointer;
    border-radius: 0.2rem;

    &:hover {
      background-color: rgb(18, 117, 87);
      color: rgb(199, 207, 214);
    }
  }
}
</style>
