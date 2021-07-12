<template>
  <main>
    <div class="main__wrapper">
      <button class="add-task">Добавить задачу</button>

      <div
        class="tasks"
      >
        <Column
        v-for="value in ColumnType"
        v-bind:key="value"
        :name="value"
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
  data() {
    return {
      ColumnType,
    };
  },
};
</script>

<style>
  main {
    flex: 1;
    display: flex;
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
  }

  .tasks {
    display: flex;
    flex: 1;
    width: 100%;
    justify-content: space-between;
    margin-top: 2rem;
  }
</style>
