<script setup>
import { ref } from 'vue';

const apiKey = ref('2ad213d1b639694377f42b93faafc162')


</script>

<template>
  <main class="main">
    <div class="container mx-auto pt-5">
      <div class="search-box">
        <input type="text" class="search-bar block w-full p-4 border-none outline-none" placeholder="search...">
      </div>
    </div>
  </main>
</template>

<style lang="scss">
.main {
  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.75));
  height: 100vh;
}

.search-bar {
  color: #313131;
  font-size: 20px;
  border-radius: 0 16px 0 16px;
  background-color: rgba(255, 255, 255, .5);
  box-shadow: 0px 0px 8px rgba(0, 0, 0, .25);
  transition: .4s;

  &:focus {
    box-shadow: 0px 0px 16px rgba(0, 0, 0, .25);
    background-color: rgba(255, 255, 255, .9);
    border-radius: 16px 0 16px 0;

  }
}
</style>