<script setup>
  import Navbar from './components/Navbar.vue';
  import MainComp from './components/MainComp.vue';
  import About from './components/About.vue';
  import { ref, onMounted } from 'vue';
  import { useStore } from 'vuex'

  const store = useStore();

  //앱이 실행되면 날씨 데이터 가져오기
  onMounted(() => {
    store.dispatch('getWeather');
  })
</script>

<template>
  <!-- <button @click="$store.dispatch('getWeather')">getWeather</button> -->
  <Navbar/>  
  <div>
    <div v-if="!$store.state.toggle">
      <MainComp/>
    </div>
    <div v-else>
      <About/>
    </div>
  </div>
</template>

<style scoped lang="scss">

</style>
