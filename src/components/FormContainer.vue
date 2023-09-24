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
  <form @submit.prevent="addItem(props.datas)" class="form-container">
    <h2 class="form-title">Ajoute des tâches</h2>
    <div class="form-item title">
      <label for="form-title">Titre : </label>
      <input
        id="form-title"
        class="form-input title"
        v-model="newItem.title"
        placeholder="titre de la tâche"
      />
    </div>
    <div class="form-item content">
      <label for="form-content">Description : </label>
      <textarea
        id="form-content"
        class="form-input content"
        v-model="newItem.content"
        placeholder="description..."
      ></textarea>
    </div>
    <button type="submit" class="form-submit">+ Ajouter</button>
  </form>
</template>

<style scoped>
form.form-container {
  background-color: rgb(51, 51, 51);
  padding: 2rem;
  display: flex;
  flex-flow: column nowrap;
  gap: 1.5rem;
  border-radius: 0.5rem;
  border: solid rgb(126, 126, 126) 2px;
  color: rgb(18, 117, 87);

  & > .form-item {
    display: flex;
    flex-flow: column;
    width: 100%;
    position: relative;
    /* overflow-x: hidden; */

    & > label {
      background-color: rgba(51, 51, 51);
      font-size: 1.1rem;
      position: absolute;
      padding: 0 0.5rem;
      top: -0.8rem;
      left: 2rem;
    }

    & > [class^='form-'] {
      border-radius: 0.5rem;
      background-color: transparent;
      border: solid rgb(126, 126, 126) 2px;
      color: rgba(234, 240, 245, 0.753);

      &:focus {
        color: aliceblue;
      }
    }
    & > .form-input.title {
      font-size: 1rem;
      padding: 1rem 0.5rem;
    }
    & > .form-input.content {
      font-family:
        Inter,
        -apple-system,
        BlinkMacSystemFont,
        'Segoe UI',
        Roboto,
        Oxygen,
        Ubuntu,
        Cantarell,
        'Fira Sans',
        'Droid Sans',
        'Helvetica Neue',
        sans-serif;
      font-size: 1rem;
      padding: 1rem 0.5rem;
    }
  }

  & > .form-title {
    text-transform: uppercase;
    font-weight: 600;
  }

  & > button.form-submit {
    width: fit-content;
    padding: 0.5rem 1rem;
    font-size: 1.5rem;
    background-color: rgb(21, 145, 108);
    border-radius: 0.5rem;
    cursor: pointer;
    transition: all 0.5s;
    color: aliceblue;

    &:hover {
      transition: all 0.5s;
      background-color: rgb(18, 117, 87);
      color: rgb(199, 207, 214);
      border-color: aliceblue;
      transform: scale(1.1);
    }
  }
}
</style>
