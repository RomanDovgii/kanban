<template>
  <form class="modal modal--hidden">
    <h2 class="modal__name">Test</h2>
    <label class="modal__label">
      Описание задачи:
      <textarea
        name="description"
        class="modal__textarea"
        placeholder="Введите описание"
      ></textarea>
    </label>

    <div class="modal__priority">
      <p class="modal__heading">Выберите приоритет задачи:</p>

      <div class="modal__radio-wr">
        <label class="modal__label-radio">
          <input type="radio" name="priority" class="modal__radio">
          1
        </label>
        <label class="modal__label-radio">
          <input type="radio" name="priority" class="modal__radio">
          2
        </label>
        <label class="modal__label-radio">
          <input type="radio" name="priority" class="modal__radio">
          3
        </label>
        <label class="modal__label-radio">
          <input type="radio" name="priority" class="modal__radio">
          4
        </label>
        <label class="modal__label-radio">
          <input type="radio" name="priority" class="modal__radio">
          5
        </label>
      </div>
    </div>

    <div class="modal__controls">
      <button type="submit" class="modal__save">Сохранить</button>
      <button class="modal__cancel">Отменить</button>
      <button class="modal__close">
        <span class="visually-hidden">Закрыть</span>
      </button>
    </div>
  </form>
</template>

<script>
export default {
  name: 'Modal',
};
</script>

<style>
  .modal {
    position: fixed;
    top: 50%;
    left: 50%;

    margin-left: -25rem;
    margin-top: -25rem;

    width: 50rem;
    height: 50rem;
    background-color: #fff;
    border: 0.3rem solid #2699FB;
    border-radius: 25px;

    display: flex;
    flex-direction: column;
    align-content: center;
    padding: 2rem;
  }

  .modal--hidden {
    display: none;
  }

  .modal__name {
    display: flex;
    justify-content: center;
    font-size: 2rem;
    text-transform: uppercase;
    color: #2699FB;
  }

  .modal__label {
    flex: 1;
    display: flex;
    flex-direction: column;
    margin-top: 3rem;
    font-size: 2rem;
    color: #2699FB;
    font-weight: 600;
  }

  .modal__textarea {
    outline: none;
    resize: none;
    width: 100%;
    flex: 1;
    margin-top: 0.5rem;
    border: 0.3rem solid #2699FB;
    border-radius: 2.5rem;
    padding: 2rem;
    font-size: 1.8rem;
    color: #2699FB;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
  }

  .modal__priority {
    margin-top: 1rem;
  }

  .modal__radio-wr {
    margin-top: 0.5rem;
    display: flex;
    margin-left: -1rem;
  }

  .modal__heading {
    font-size: 2rem;
    color: #2699FB;
    font-weight: 600;
  }

  .modal__radio {
    margin-right: 1rem;
  }

  .modal__label-radio {
    margin-left: 2rem;
    display: flex;
    align-items: center;

    font-size: 1.5rem;
    color: #2699FB;;
  }

  .modal__controls {
    margin-top: 1rem;
    flex: 1;

    display: flex;
    flex-direction: column;
    justify-content: flex-end;
  }

  .modal__save:hover,
  .modal__cancel:hover,
  .modal__close:hover,
  .modal__save:focus,
  .modal__cancel:focus,
  .modal__close:focus {
    opacity: 0.8;
  }

  .modal__save:active,
  .modal__cancel:active,
  .modal__close:active {
    opacity: 0.3;
  }

  .modal__save,
  .modal__cancel {
    background: none;
    border: none;

    background-color: #2699FB;
    color: #fff;
    border-radius: 25px;
    font-size: 1.8rem;
    padding: 1rem;

    cursor: pointer;
    transition: opacity 0.3s;

    margin-top: 1rem;
  }

  .modal__close {
    background: none;
    border: none;

    position: absolute;
    top: 1rem;
    right: 1rem;

    width: 3rem;
    height: 3rem;
    display: flex;
    justify-content: center;
    transition: opacity 0.3s;
    align-items: center;
    cursor: pointer;
  }

  .modal__close::before,
  .modal__close::after {
    content: '';
    position: absolute;

    display: block;
    height: 3px;
    width: 2rem;
    background-color: #2699FB;
    border-radius: 25px;
  }

  .modal__close::before {
    transform: rotate(45deg);
  }

  .modal__close::after {
    transform: rotate(-45deg);
  }
</style>
