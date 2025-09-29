<script setup>
import {ref} from 'vue'
//нужно написать логику для вывода уровня
//будет счетчик подед. После каждой победы + exp. if winstreak === 3. обнуляем счетчик и повышаем lvl

const props = defineProps({
  lvl: Number
})

</script>

<template>
  <div class="levelContainer">
    <div>
      <p>Уровень: {{ lvl }}</p>
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

