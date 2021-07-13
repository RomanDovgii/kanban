<template>
  <main
    :class="{'dark' : (theme === 'dark')}"
  >
    <div class="main__wrapper">
      <button
        class="add-task"
        v-on:click="handleModal"
        :class="{'add-task--dark' : (theme === 'dark')}"
      >Добавить задачу</button>

      <div
        class="tasks"
      >
        <Column
        v-for="value in ColumnType"
        v-bind:key="value"
        :name="value"
        :cards="getProperCards(cards, value)"
        :handleChangeCard="handleChangeCard"
        :deleteTask="deleteTask"
        :moveRight="moveRight"
        :moveLeft="moveLeft"
        :theme="theme"
        :startDrag="startDrag"
        :onDrop="onDrop"
        />
      </div>
    </div>
  </main>
</template>
<script>
import Column from '../column/column.vue';
import { ColumnType } from '../../utils/const';

export default {
  name: 'Main',
  components: {
    Column,
  },
  props: [
    'cards',
    'handleModal',
    'handleChangeCard',
    'deleteTask',
    'moveRight',
    'moveLeft',
    'theme',
    'startDrag',
    'onDrop',
  ],
  data() {
    return {
      ColumnType,
    };
  },
  methods: {
    getProperCards(cards, cardType) {
      return cards.filter((card) => card.type === cardType);
    },
  },
};
</script>

<style>
  main {
    flex: 1;
    display: flex;
    transition: background-color 0.3s;
  }

  .dark {
    background-color: rgb(31, 31, 31);
  }

  .main__wrapper {
    max-width: 1200px;
    width: 100%;
    margin: 0 auto;
    padding: 20px 0;

    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .add-task {
    background: none;
    border: none;
    outline: none;

    padding: 10px 20px;
    background-color: #2699FB;
    border-radius: 25px;

    color: #fff;
    font-size: 2rem;
    font-weight: 600;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .add-task--dark {
    background-color: #001930;
  }

  .tasks {
    display: flex;
    flex: 1;
    width: 100%;
    justify-content: space-between;
    margin-top: 2rem;
  }
</style>
