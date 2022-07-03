<script setup>
import Title from '@/components/Title.vue'
</script>

<template>
  <header>
    <div class="wrapper" style="width: 100%">
      <Title title="CALCULATOR" />
    </div>
  </header>

  <RouterView />
</template>

<style>
@import '@/assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

.form {
  width: 100%;
  padding: 10px
}

.form .form-control{
  margin-top: 5px;
}

.form .input{
  font-family: inherit;
  padding: 0.1em 0.2em;
  border-radius: 10px;
}
</style>
