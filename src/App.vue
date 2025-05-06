<script setup>
import PortfolioMain from './pages/PortfolioMain.vue';
import PageHeader from './components/PageHeader.vue';
</script>

<template>
  <header>
    <PageHeader/>
  </header>

  <main>
    <PortfolioMain />
  </main>
</template>

<style scoped>
  header{
    width: 100%;
    line-height: 60px;
  }

  main {
    width: 100%;
    margin: 0;
    padding: 0;
    overflow-x: hidden;
  }
</style>
