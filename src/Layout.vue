<script setup>
const props = defineProps({
  lvl: Number
})
</script>

<template>
  <header>
    <nav>
      <ul>
        <li>
          <div class="lvl"> Уровень: {{ lvl }}</div>
        </li>
        <li><a href="#"><img src="../public/favicon.ico" alt=""></a></li>
      </ul>
    </nav>
  </header>
</template>

<style scoped>
a {
  text-decoration: none;
  color: black;
}

ul {
  list-style: none;
  background: #68904D;
  display: flex;
  justify-content: end;
}

li {
  padding: 10px 30px;
}

img {
  width: 50px;
  height: 70px;
  background: #fff;
  border: 4px solid #8ea6b7;
  border-radius: 10px;
}

.lvl {

}
</style>