<script setup lang="ts">
import { ref, onMounted } from 'vue'
import axios from 'axios'

const roomAlphabet = ref('')

const getRoomAlphabet = async () => {
  try {
    const endpoint = 'https://script.google.com/macros/s/AKfycbwf1ITlkGdOyMiorjhuBXcFJEVeWkim49WiFa5VR2Fs_HfJbzdklTBOom0ZLXe_YLZq6g/exec';
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
      <a href="http://">ブレイクアウトルーム部屋数調整</a>
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
