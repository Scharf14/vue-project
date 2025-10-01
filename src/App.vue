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
  {id: 4, film_file_path: '...', difficult_id: 1, name: 'Кунг-фу панда', emojies: '🐼🥋🍜'},
  {id: 5, film_file_path: '...', difficult_id: 1, name: 'Алладин', emojies: '🧞‍♂️🔮🌴'},
  {id: 6, film_file_path: '...', difficult_id: 1, name: 'Рататуй', emojies: '🐀👦🍳'},
  {id: 7, film_file_path: '...', difficult_id: 1, name: 'В поисках Немо', emojies: '🐠🐟🔍'},
  {id: 8, film_file_path: '...', difficult_id: 2, name: 'Один дома', emojies: '👦🏠✈️'},
  {id: 9, film_file_path: '...', difficult_id: 3, name: 'Трое в лодке, не считая собаки', emojies: '3️⃣🚣🐕'},
  {id: 10, film_file_path: '...', difficult_id: 1, name: 'Охотники за привидениями', emojies: '👻🚫'},
  {id: 11, film_file_path: '...', difficult_id: 1, name: 'Крепкий орешек', emojies: '💪🥜'},
  {id: 12, film_file_path: '...', difficult_id: 3, name: 'Достучаться до небес', emojies: '👊☁️'},
  {id: 13, film_file_path: '...', difficult_id: 3, name: 'Молчание ягнят', emojies: '🔇🐑'},
  {id: 14, film_file_path: '...', difficult_id: 3, name: 'Планета обезьян', emojies: '🌍🐒'},
  {id: 15, film_file_path: '...', difficult_id: 3, name: 'В джазе только девушки', emojies: '🎺👩‍❤️‍👩'},
  {id: 16, film_file_path: '...', difficult_id: 2, name: 'Пила', emojies: '🪚⚰️'},
  {id: 17, film_file_path: '...', difficult_id: 2, name: 'Хороший, плохой, злой', emojies: '😇😈😠'},
  {id: 18, film_file_path: '...', difficult_id: 2, name: 'Эдвард Руки-ножницы', emojies: '👦🏻👐🏻✂️'}
])

// const difficult = ref([
//   {id: 0, exp: 100, name: '...'}
// ])
// const levels = ref([
//   {id: 0, name: '...', difficult_id: 0, winstreak: 0}
// ])
// const users = ref([
//   {id: 0, avatar_path: '...', name: '..', exp: 100}
// ])

const rand = Math.floor(Math.random() * films.value.length)

//Добавить в localstorage
const progress = ref({
  lvl: 0,
  winStreak: 0
})

// localStorage.setItem('progress', JSON.stringify(progress.value))
// const localProgress = JSON.parse(localStorage.getItem('progress'))


const correctFilm = ref(films.value[rand])
const emoji = ref(correctFilm.value.emojies)

function getRandomFilm() {
  const randomIndex = Math.floor(Math.random() * films.value.length)
  return films.value[randomIndex]
}

function createAnswerOptions() {
  const answerOptions = []


  while (answerOptions.length < 2) {
    const randomIndex = Math.floor(Math.random() * films.value.length)
    const wrongFilm = films.value[randomIndex]

    if (wrongFilm.name !== correctFilm.value.name && !answerOptions.includes(wrongFilm.name)) {
      answerOptions.push(wrongFilm.name)
    }
  }
  const randomIndexOptions = Math.floor(Math.random() * films.value.length)
  answerOptions.splice(randomIndexOptions, 0, correctFilm.value.name)

  return answerOptions
}

const answerOptions = ref(createAnswerOptions())

function changeFilm(answer) {
  if (answer === correctFilm.value.name) {
    progress.value.winStreak++
  } else {
    progress.value.winStreak = 0
  }
  correctFilm.value = getRandomFilm()
  emoji.value = correctFilm.value.emojies
  answerOptions.value = createAnswerOptions()
  console.log(progress.value.winStreak)

}


</script>

<template>
  <div class="container">
    <Layout
        class="component-card layout"
        :lvl="progress.lvl"
    >

    </Layout>

    <div class="stats-row">
      <Level
          class="component-card level"
          :lvl="progress.lvl"
      >

      </Level>

      <Winstreak
          class="component-card winstreak"
          :winStreak="progress.winStreak"
      >

      </Winstreak>
    </div>

    <Emoji
        class="component-card emoji-container"
        :emoji="emoji"
    />

    <AnswerOptions
        class="component-card answer-options"
        :answerOptions="answerOptions"
        @sendAnswer="changeFilm"

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

