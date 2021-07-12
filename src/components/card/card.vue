<template>
  <div class="card">
    <h3 class="card__number">Test</h3>
    <p class="card__description">
      Lorem ipsum, dolor sit amet consectetur
      adipisicing elit. Voluptates dolores, quis ullam minus pariatur
      velit consectetur, commodi, saepe veniam reprehenderit blanditiis
      iusto quod aspernatur ipsam provident dolore illo eius distinctio?
    </p>
    <p class="card__priority card__priority--high">1</p>
    <p class="card__date">12.03.2020</p>
    <div class="card__controls">
      <button class="card__edit">Изменить</button>
      <button class="card__delete">Удалить</button>
      <button class="card__left">Переместить влево</button>
      <button class="card__right">Переместить вправо</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
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

    color: #fff;
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
