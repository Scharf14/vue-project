<script setup>
import {ref} from 'vue'

const winstreak = ref(0);
</script>

<template>
  <div class="win-container">
    <div>
      <p>Винстрик: {{ winstreak }}</p>
    </div>
  </div>
</template>

<style scoped>
.win-container {
  margin-top: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: cadetblue;
}

</style>