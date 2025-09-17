<script setup>
import {ref} from 'vue'
//нужно написать логику для вывода уровня
//будет счетчик подед. После каждой победы + exp. if winstreak === 3. обнуляем счетчик и повышаем lvl
</script>

<template>
  <div class="levelContainer">
    <div>
      <p>Уровень: {{ level }}</p>
    </div>
  </div>
</template>

<style scoped>
.levelContainer {
  margin-top: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: cadetblue;
}

</style>

