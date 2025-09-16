<script setup>

</script>

<template>
  <div class="options-container">
    <div class="main-bar">
      <p>Варианты ответа</p>
      <div class="answers">
        <p>вариант 1</p>
        <p>вариант 2</p>
        <p>вариант 3</p>
      </div>
    </div>
  </div>
</template>

<style>
  .options-container {
    margin-top: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .main-bar {
   background: #EE9B01;
    width: 60%;
    height: 300px;
    text-align: center;
    border-radius: 30px;
  }

  .main-bar > p {
    padding-top: 50px;
    font-size: 30px;
    font-weight: 500;
  }

  .answers {
    display: flex;
    justify-content: space-around;
    margin-top: 90px;
  }

  .answers p {
    background: #68904D;
    width: 200px;
    height: 30px;
    border-radius: 10px;

  }


</style>