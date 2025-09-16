
<script setup>
import { ref } from 'vue'
import Level from './Level.vue'
import Winstreak from './Winstreak.vue';
import AnswerOptions from './AnswerOptions.vue';
import Layout from './Layout.vue';
import Emoji from './Emoji.vue'

const songs = ref([
  {id: 0, audio_file_path: '...', difficult_id: 1, name: '...', emojies: '🚢🧊💔'},
])
const difficult = ref([
  {id: 0, exp: 100, name: '...'}
])
const levels = ref([
  {id:0, name: '...', difficult_id: 0, winstreak: 0}
])
const users = ref([
  {id: 0, avatar_path: '...', name: '..', exp: 100}
])

</script>

<template>

      <Layout>

      </Layout>
  <div class="container">
      <Level>

      </Level>

      <Winstreak>

      </Winstreak>

      <Emoji>

      </Emoji>

      <AnswerOptions>

      </AnswerOptions>
  </div>
</template>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>

