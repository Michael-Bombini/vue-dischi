<template>
  <div id="app d-flex flex-column">
    <TheHeader/>
    <DiskContainer/>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import DiskContainer from './components/DiskContainer.vue';

export default {
  name: 'App',
  components: {
    TheHeader,
    DiskContainer
}
}
</script>

<style lang="scss">

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}






</style>
