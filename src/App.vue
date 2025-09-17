<script setup>
import {ref} from 'vue'
import Level from './Level.vue'
import Winstreak from './Winstreak.vue';
import AnswerOptions from './AnswerOptions.vue';
import Layout from './Layout.vue';
import Emoji from './Emoji.vue'

const films = ref([
  {id: 0, film_file_path: '...', difficult_id: 1, name: 'Титаник', emojies: '🚢🧊💔'},
  {id: 1, film_file_path: '...', difficult_id: 1, name: 'Гарри Подтёр', emojies: '🧙‍♂️⚡️👓'},
  {id: 2, film_file_path: '...', difficult_id: 1, name: 'Принцесса и лягушка', emojies: '👸🐸💋'},
  {id: 3, film_file_path: '...', difficult_id: 2, name: 'Одержимость', emojies: '🥁🔥'},
  {id: 4, film_file_path: '...', difficult_id: 2, name: 'Кунг-фу панда', emojies: '🐼🥋🍜'},
  {id: 5, film_file_path: '...', difficult_id: 2, name: 'Алладин', emojies: '🧞‍♂️🔮🌴'},
  {id: 6, film_file_path: '...', difficult_id: 3, name: 'Рататуй', emojies: '🐀👦🍳'},
  {id: 7, film_file_path: '...', difficult_id: 3, name: 'В поисках Немо', emojies: '🐠🐟🔍'},
  {id: 8, film_file_path: '...', difficult_id: 3, name: 'Один дома', emojies: '👦🏠✈️'},
])

const difficult = ref([
  {id: 0, exp: 100, name: '...'}
])
const levels = ref([
  {id: 0, name: '...', difficult_id: 0, winstreak: 0}
])
const users = ref([
  {id: 0, avatar_path: '...', name: '..', exp: 100}
])

function createPost(a, b) {
  console.log(a, b)
}
function increment() {

}
//создать функцию, с помощью который мы будем выводить эмоции в зависимости от difficult_id.
//Проблема теперь в том, что нужно как-то получить difficult_id.

// function sendEmoji() {
//   films.value.forEach((e, index) => {
//     if(films[index].difficult_id)
//   })
// }
const rand = Math.floor(Math.random()* films.value.length)
</script>

<template>
  <div class="container">
    <Layout>

    </Layout>

    <Level>

    </Level>

    <Winstreak>

    </Winstreak>

    <Emoji :emoji="films[rand].emojies">

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

.container {
  background: #f5f3ef;

}
</style>

