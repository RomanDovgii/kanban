<template>
  <div
    class="cards-column"
    :class="{'cards-column--dark' : (theme === 'dark')}"
  >

      <h3
        class="cards-column__name"
        :class="{'cards-column__name--dark' : (theme === 'dark')}"
        >
        {{name}}
      </h3>

      <div
        class="cards-column__cards"
        >
        <Card
        v-for="card in cards"
        v-bind:key="card"
        :card="card"
        :handleChangeCard="handleChangeCard"
        :deleteTask="deleteTask"
        :moveRight="moveRight"
        :moveLeft="moveLeft"
        :theme="theme"
        />
      </div>
  </div>
</template>

<script>
import Card from '../card/card.vue';

export default {
  name: 'Column',
  components: {
    Card,
  },
  props: [
    'name',
    'cards',
    'handleChangeCard',
    'deleteTask',
    'moveRight',
    'moveLeft',
    'theme',
  ],
};
</script>

<style>
  .cards-column {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-left: 1rem;
    margin-right: 1rem;
    background-color: #F1F9FF;
    transition: background-color 0.3s;
    border-radius: 25px;
  }

  .cards-column--dark {
    background-color: #707070;
  }

  .cards-column__name {
    font-size: 2rem;
    color: #fff;
    width: 100%;
    padding: 2rem 1rem;

    border-top-right-radius: 25px;
    border-top-left-radius: 25px;
    display: flex;
    justify-content: center;

    background-color: #2699FB;
  }

  .cards-column__name--dark {
    background-color: #01203b;
  }
</style>
