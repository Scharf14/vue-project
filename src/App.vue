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

const rand = Math.floor(Math.random() * films.value.length)

//Добавить в localstorage
const lvl = ref(0)
const winStreak = ref(0)

const correctFilm = films.value[rand]
const emoji = ref(correctFilm.emojies)

console.log('Правильный фильм:', correctFilm.name)
console.log('Эмодзи:', emoji.value)

function createAnswerOptions() {
  const answerOptions = []


  while (answerOptions.length < 2) {
    const randomIndex = Math.floor(Math.random() * films.value.length)
    const wrongFilm = films.value[randomIndex]

    if (wrongFilm.name !== correctFilm.name && !answerOptions.includes(wrongFilm.name)) {
      answerOptions.push(wrongFilm.name)
    }
  }
  const randomAnswerOptions = Math.floor(Math.random() * films.value.length)
  answerOptions.splice(randomAnswerOptions, 0, correctFilm.name)
  return answerOptions
}

const answerOptions = createAnswerOptions()
console.log(answerOptions)
// function shuffle() {
//   const rand = Math.floor(Math.random() * answerOptions.length)
//   console.log(answerOptions)
// }
// shuffle()

//ну давай по другому, берешь рандомное число в пределах длины массива, вставляешь правильный ответ на это место.
// Если правильный ответ стал крайним - ничего больше можно не менять, если нет, то можно рандомно либо элемент,
// который в конце, перемещать на 1 место, либо наоборот
</script>

<template>
  <div class="container">
    <Layout
        class="component-card layout"
        :lvl="lvl"
    >

    </Layout>

    <div class="stats-row">
      <Level
          class="component-card level"
          :lvl="lvl"
      >

      </Level>

      <Winstreak
          class="component-card winstreak"
          :winStreak="winStreak"
      >

      </Winstreak>
    </div>

    <Emoji
        :emoji="emoji"
        class="component-card emoji-container"
    />

    <AnswerOptions
        class="component-card answer-options"
        :answerOptions="answerOptions"
    >

    </AnswerOptions>

  </div>
</template>

<style>
* {
  padding: 0;
  margin: 0;
}

.container {
  min-height: 100vh;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  padding: 20px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

/* Общий стиль для всех компонентов */
.component-card {
  background: white;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 20px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  border: 1px solid #e1e5e9;
}

/* Специфичные стили для каждого компонента */
.layout {
  background: linear-gradient(135deg, cadetblue 0%, #5f9ea0 100%);
  color: white;
  text-align: center;
}

.level {
  background: #68904D;
  color: white;
  font-weight: bold;
}

.winstreak {
  background: #EE9B01;
  color: white;
  font-weight: bold;
}

.emoji-container {
  text-align: center;
  font-size: 3rem;
  background: #f8f9fa;
  border: 2px dashed #68904D;
}

/* Стили для вариантов ответов */
.answer-options {
  background: white;
}

/* Состояния для правильных/неправильных ответов */
.correct {
  border: 3px solid #68904D;
  background: #f0f9f0;
}

.incorrect {
  border: 3px solid #dc3545;
  background: #fdf2f2;
}

.feedback {
  text-align: center;
  padding: 10px;
  margin-top: 10px;
  border-radius: 6px;
  font-weight: bold;
}

.feedback.correct {
  color: #68904D;
  background: #f0f9f0;
}

.feedback.incorrect {
  color: #dc3545;
  background: #fdf2f2;
}
</style>

