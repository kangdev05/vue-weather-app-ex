<template>
  <div class="search-bar">
    <form @submit.prevent>  <!-- 폼전송 이벤트 방지-->
      <div class="form-group">
        <input @input="inputText=$event.target.value" type="search" placeholder="지역을 입력해 주세요">
        <button @click="$store.commit('onSearchCity', inputText); $store.dispatch('getWeather')">
          <font-awesome-icon class="icon" :icon="['fas', 'magnifying-glass']" />
        </button>
      </div>
    </form>
  </div>
  <!-- <p>{{ inputText }}</p> -->
</template>

<script setup>
//ref(): 상태변수를 정의하고 검색어 입력값을 저장합니다.
//defineEmits():하위 컴포넌트에서 이벤트가 발생하면 상위 컴포넌트에 전달합니다.
  import { ref } from 'vue';

  const inputText = ref('');
  // const emits = defineEmits(['onSearchCity']);  //이벤트를 정의하고 함수를 반환
</script>
  
<style lang="scss" scoped>
  .search-bar {
    padding: 8px 20px;
    border-radius: 40px;
    background: #fff;
    border: 1px solid #ccc;
    padding: 0 20px;
  
    form {
      .form-group {
        display: flex;
        input {
          width: 100%;
          border: none;
          padding: 1em 0;
          font-size: 18px;
          outline: none;
        }
        button {
          background: transparent;
          border: none;
          &:hover { cursor: pointer; }
          .icon { font-size: 24px; }
        }
      }
    }
  }
</style>