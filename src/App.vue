<script setup lang="ts">
import InputGrid from './components/InputGrid.vue';
import Navbar from './components/Navbar.vue';
</script>

<template>
  <div class="app-wrapper">
    <Navbar class="nav"/>
    <div class="input-grid-wrapper">
      <InputGrid />
    </div>

    <div class="green"></div>
    <div class="red"></div>
  </div>
</template>

<style scoped>
.app-wrapper{
  display: flex;
  flex-direction: column;
  
}
.nav{
}
.input-grid-wrapper{
  display: flex;
  align-items: center;
/* justify content makes left side get cut off*/
margin-top: 8rem;
  margin-bottom: 4rem;
  overflow-x: auto;

}
@media screen and (max-width: 450px){
  .input-grid-wrapper{
    margin-top: 12rem;
  }
}
@media screen and (max-width: 340px){
  .input-grid-wrapper{
    margin-top: 16rem;
  }
}

</style>
