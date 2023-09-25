<script setup>
const props = defineProps(['datas', 'deleteData']);
</script>

<template>
  <ul class="list-container" v-if="props.datas.length > 0">
    <li class="list-element" v-for="data in props.datas" :key="data.id">
      <h3 class="list-title">
        <input class="list-check" type="checkbox" v-model="data.done" />
        <span :class="{ done: data.done }">{{ data.title }}</span>
        <button class="list-delete" @click="deleteData(data.id)">X</button>
      </h3>
      <article>
        <h2>Description :</h2>
        <p class="list-content">{{ data.content }}</p>
      </article>
    </li>
  </ul>
</template>

<style scoped>
.done {
  text-decoration: line-through;
  color: rgba(234, 240, 245, 0.753);
}

.list-check {
  width: 2rem;
}

.list-container {
  border: solid rgb(126, 126, 126) 2px;
  border-radius: 0.5rem;
  padding: 3rem;
  background-color: rgb(51, 51, 51);
  list-style-type: none;
  display: flex;
  flex-flow: column wrap;

  @media screen and (min-width: 768px) {
    width: 100%;
  }

  & > .list-element {
    & > .list-title {
      & > button {
        color: aliceblue;
        background-color: rgb(201, 43, 38);
        cursor: pointer;
        border: none;
        padding: 0.5rem;
        height: 1.8rem;
        width: 1.8rem;
        text-align: center;
        border-radius: 0.2rem;
        float: right;

        &:hover {
          background-color: rgb(155, 40, 37);
        }
      }
      & > span {
        font-size: 2rem;
        font-weight: 600;
      }
    }

    & > article {
      & > h2 {
        color: rgb(21, 145, 108);
      }
      & > .list-content {
        color: rgba(234, 240, 245, 0.753);
      }
    }
  }
}
</style>
