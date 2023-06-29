<template>
  <div id="app" class="container">
    <h1 class="pageHeading">Smartphone Table</h1>
    <SmartphoneTable />
  </div>
</template>

<style>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  margin-top: 20px; /* Optional: Add some top margin for spacing */
  background-color: white; /* Updated background color */
}
</style>

<script>
import SmartphoneTable from './components/ResponsiveTable.vue';

export default {
  name: 'App',
  components: {
    SmartphoneTable,
  },
};
</script>

<style>
.pageHeading{
  font-weight: 800;
  font-size: 60px;
  color: #3A1303;
}
</style>
