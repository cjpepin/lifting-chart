<script setup lang="ts">
import InputGrid from './components/InputGrid.vue';
import Navbar from './components/Navbar.vue';
</script>

<template>
  <div>
    <Navbar class="nav"/>
    <div class="input-grid-wrapper">
      <InputGrid />
    </div>
  </div>
</template>

<style scoped>
.nav{
  margin-top: -8rem;
}
.input-grid-wrapper{
  display: flex;
  align-items: center;
  justify-content: center;

  margin-top: 8rem;
}

</style>
