<script setup lang="ts">
import { ref, onMounted } from 'vue'
import axios from 'axios'

const roomAlphabet = ref('')

const getRoomAlphabet = async () => {
  try {
    const endpoint = 'https://script.google.com/macros/s/AKfycbzFe8mLzSOYuYURrAoCsR9gCOGx0v_IkK_GD-qLLxuG8kYeU7OUIL2Ph2rxBUl0ht2BoQ/exec';
    const response = await axios.get(endpoint);
    roomAlphabet.value = response.data;
  } catch (error) {
    console.error('Error fetching room alphabet:', error);
  }
}

onMounted(getRoomAlphabet)
</script>

<template>
  <div id="app">
    <div class="content">
      <h1>あなたのブレイクアウトルームのテーブルは?</h1>
      <p>{{ roomAlphabet }}</p>
      <a href="https://docs.google.com/spreadsheets/d/1e8BMErQ5ZjZmexTv3VfLQCR4U_tjeyHn4TGrSc0wUAk/edit?usp=sharing">ブレイクアウトルーム部屋数調整</a>
    </div>
  </div>
</template>

<style scoped>
#app {
  width: 100vw;
  height: 100vh;
}
.content {
  width: 90%;
  height: 90%;
  margin: auto;
}
h1 {
  display: block;
}

p {
  width: 25rem;
  font-size: 25rem;
  margin: 1rem auto 0;
}
</style>
