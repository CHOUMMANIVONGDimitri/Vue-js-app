<script setup></script>

<template>
  <h2 class="footer-title">Mes Informations</h2>
  <ul class="footer-links">
    <li>
      <a
        href="https://www.linkedin.com/in/dimitri-choummanivong-507669228/"
        target="_blank"
        rel="noopener noreferrer"
        >LinkedIn</a
      >
    </li>
    <li>
      <a href="https://github.com/CHOUMMANIVONGDimitri" target="_blank" rel="noopener noreferrer"
        >Github</a
      >
    </li>
    <li>
      <a href="mailto:dimitrichoummanivong@gmail.com">M'envoyer un e-mail</a>
    </li>
  </ul>
  <hr class="footer-separator" />
  <p class="footer-rigths">TodoApp™ version 1.0.0, CHOUMI © . Tous droits réservés.</p>
</template>

<style scoped>
.footer-title {
  margin-bottom: 2rem;
}

.footer-separator {
  margin-bottom: 1rem;
}
.footer-links {
  list-style-type: none;
  padding-bottom: 1rem;
  & > li > a {
    color: rgb(21, 145, 108);
  }
}
</style>
