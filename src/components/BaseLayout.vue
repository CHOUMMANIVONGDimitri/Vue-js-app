<script setup></script>

<template>
  <header class="layout-header">
    <slot name="header"></slot>
  </header>
  <main class="layout-main">
    <slot></slot>
  </main>
  <footer class="layout-footer">
    <slot name="footer"></slot>
  </footer>
</template>

<style scoped>
[class^='layout-'] {
  color: aliceblue;
  background-color: rgb(39, 39, 39);
  padding: 1.5rem 1rem;
}
.layout-header {
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  min-height: 20vh;
  background: linear-gradient(0deg, rgb(39, 39, 39) 0%, rgb(15, 124, 91) 100%);
}
.layout-main {
  min-height: 60vh;
  display: flex;
  flex-flow: column nowrap;
  gap: 2rem;
  @media screen and (min-width: 768px) {
    flex-flow: row nowrap;
    padding-bottom: 5rem;
  }
}
.layout-footer {
  color: rgb(56, 56, 56);
  min-height: 20vh;
  background-color: aliceblue;
}
</style>
