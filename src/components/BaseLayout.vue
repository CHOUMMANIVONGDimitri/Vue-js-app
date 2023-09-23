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
.layout-header {
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  min-height: 20vh;
}
.layout-main {
  min-height: 60vh;
}
.layout-footer {
  min-height: 20vh;
}

[class^='layout-'] {
  border: solid rgb(0, 60, 255) 1px;
  color: aliceblue;
  background-color: rgb(39, 39, 39);
  padding: 1.5rem 1rem;
}
</style>
