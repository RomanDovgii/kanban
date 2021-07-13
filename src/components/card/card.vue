<template>
  <div
    class="card"
    :class="{'card--dark' : (theme === 'dark')}"
    draggable="true"
    @dragstart="startDrag($event, card)">
    <h3 class="card__number">Задача № {{card.id}}</h3>
    <p class="card__description">
      {{card.description}}
    </p>
    <p
      class="card__priority"
      :class="{
        'card__priority--low': (card.priority == 1),
        'card__priority--below-middle': (card.priority == 2),
        'card__priority--middle': (card.priority == 3),
        'card__priority--upper-middle': (card.priority == 4),
        'card__priority--high': (card.priority == 5),
      }"
    >{{card.priority}}</p>
    <p class="card__date">{{new Date(card.date).toLocaleDateString("ru-ru")}}</p>
    <div
      class="card__controls"
      :class="{'card__controls--dark' : (theme === 'dark')}"
    >
      <button
        class="card__edit"
        v-on:click="handleChangeCard(card.id)"
      >Изменить</button>
      <button
        class="card__delete"
        v-on:click="deleteTask(card.id)"
      >Удалить</button>
      <button
        class="card__left"
        :disabled="card.type === ColumnType.PLANNED"
        v-on:click="moveLeft(card.id)"
      >Переместить влево</button>
      <button
        class="card__right"
        :disabled="card.type === ColumnType.DONE"
        v-on:click="moveRight(card.id)"
      >Переместить вправо</button>
    </div>
  </div>
</template>

<script>
import { ColumnType } from '../../utils/const';

export default {
  name: 'Card',
  props: [
    'card',
    'handleChangeCard',
    'deleteTask',
    'moveRight',
    'moveLeft',
    'theme',
    'startDrag',
  ],
  data() {
    return {
      ColumnType,
    };
  },
};
</script>

<style>
  .card {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 1rem 2rem;
    padding: 2rem;
    background-color: #fff;
    border: 2px solid #2699FB;
    border-radius: 25px;
    position: relative;
  }

  .card--dark {
    background-color: #001930;
    border: 2px solid #fff;
  }

  .card--dark h3,
  .card--dark p {
    color: #fff;
  }

  .card--dark p.card__priority {
    color: #000;
  }

  .card__number {
    font-size: 2rem;
    color: #2699FB;
    font-weight: 600;
    text-transform: uppercase;
  }

  .card__description {
    font-size: 1.8rem;
    color: #2699FB;
    margin-top: 1rem;
  }

  .card__priority {
    position: absolute;
    top: 1.5rem;
    left: 2rem;

    width: 3rem;
    height: 3rem;

    background-color: #2699FB;
    border-radius: 50%;

    color: #000;
    font-size: 1.6rem;

    display: flex;
    justify-content: center;
    align-items: center;
  }

  .card__priority--low {
    background-color: rgb(123, 255, 96);
  }

  .card__priority--below-middle {
    background-color: rgb(222, 253, 82);
  }

  .card__priority--middle {
    background-color: rgb(255, 252, 96);
  }

  .card__priority--upper-middle {
    background-color: rgb(255, 205, 96);
  }

  .card__priority--high {
    background-color: rgb(255, 96, 96);
  }

  .card__date {
    font-size: 1.8rem;
    color: #2699FB;
    margin-top: 1rem;
  }

  .card__controls {
    margin-top: 2rem;

    display: flex;
    flex-wrap: wrap;
  }

  .card__controls--dark button {
    background-color: #003b72;
  }

  .card__edit,
  .card__delete,
  .card__left,
  .card__right {
    background: none;
    border: none;

    background-color: #2699FB;
    color: #fff;
    border-radius: 25px;
    font-size: 1.8rem;
    padding: 1rem;

    cursor: pointer;
    transition: opacity 0.3s;
  }

  .card__edit:hover,
  .card__delete:hover,
  .card__left:hover,
  .card__right:hover,
  .card__edit:focus,
  .card__delete:focus,
  .card__left:focus,
  .card__right:focus {
    opacity: 0.8;
  }

  .card__edit:active,
  .card__delete:active,
  .card__left:active,
  .card__right:active {
    opacity: 0.3;
  }

  .card__edit:disabled,
  .card__delete:disabled,
  .card__left:disabled,
  .card__right:disabled {
    opacity: 0.2;
  }

  .card__edit {
    width: 100%;
  }

  .card__delete {
    width: 100%;
    margin-top: 0.5rem;
  }

  .card__left,
  .card__right {
    flex: 1;

    margin-top: 0.5rem;
  }

  .card__left {
    margin-right: 0.5rem;
  }

  .card__right {
    margin-left: 0.5rem;
  }
</style>
