<template>
  <header
    class="header"
    :class="{'header--dark' : (theme === 'dark')}">
    <div class="header__wrapper">
      <a class="header__logo-link">
        <svg width="50" class="header__logo" viewBox="0 0 256 178" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid"><path d="M0 63.228l119.833 63.23v50.744L0 113.972V63.227zM119.834 0L8.994 58.483 57.08 83.855l62.754-33.111V0zm16.333 0v50.744L207.914 88.6l-71.747 37.856v50.744L256 113.971V63.229L136.167 0z" fill="currentColor"/></svg>
      </a>
      <h1 class="header__project-name">Канбан</h1>

      <div class="header__theme">
        <input
          id="theme"
          type="checkbox"
          name="theme"
          class="header__theme-switcher"
          v-on:change="changeTheme">
        <label for="theme" class="header__label">
          Изменить тему
        </label>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: [
    'changeTheme',
    'theme',
  ],
};
</script>

<style>
  .header {
    background-color: #2699FB;
    min-height: 5vh;
    transition: background-color 0.3s;
  }

  .header--dark {
    background-color: #001930;
  }

  .header__wrapper {
    max-width: 1200px;
    width: 100%;
    margin: 0 auto;
    padding: 15px 0;

    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .header__logo-link,
  .header__project-name,
  .header__theme {
    flex: 1;
  }

  .header__logo,
  .header__project-name,
  .header__label {
    color: #fff;
  }

  .header__project-name {
    display: flex;
    justify-content: center;
  }

  .header__theme {
    display: flex;
    justify-content: flex-end;
  }

  .header__theme-switcher {
    display: none;
  }

  .header__project-name {
    font-size: 3rem;
  }

  .header__label {
    display: flex;
    flex-direction: column;
    align-items: center;

    cursor: pointer;

    font-size: 1.5rem;
  }

  .header__label::after {
    content: '';
    display: block;
    height: 20px;
    width: 40px;
    margin-top: 10px;

    background-color: #fff;
  }
</style>
