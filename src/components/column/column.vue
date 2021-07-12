<template>
  <div class="cards-column">
      <h3 class="cards-column__name">
        {{name}}
      </h3>

      <div class="cards-column__cards">
        <Card/>
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

    border-radius: 25px;
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
</style>
