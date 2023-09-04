<script setup>
import Navbar from "./components/Navbar.vue";
import Filter from "./components/Filter.vue";
import StatusSummary from "./components/StatusSummary.vue";
import ValuationBanner from "./components/ValuationBanner.vue";
let make = 'Abarth 595';
let family = '';
</script>

<template>
  <div class="app">
    <div class="navbar-container">
      <Navbar />
    </div>
    <div class="main">
      <div class="title">
        <h1 class="headline">Search Used Car Prices</h1>
      </div>
      <div class="filter">
        <Filter />
      </div>
      <div>
        <StatusSummary :title="`${make} ${family}`"/>
      </div>
      <div>
        <ValuationBanner />
      </div>
      <div class="result">
        <RouterView />
      </div>
    </div>

  </div>
</template>

<style scoped>
.app {
  align-items: center;
  justify-content: center;
}

.navbar-container {
  width: 100%;
  text-align: center;
}

.headline {
  font-weight: bold;
}

.main {
  width: 100%;
  margin: 5px;
  padding: 5px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.main div {
  width: 1400px;
}

.title {
  display: block;
  flex: none;
}
</style>