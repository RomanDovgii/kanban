<template>
  <footer
    class="footer"
    :class="{'footer--dark' : (theme === 'dark')}"
  >
    <section class="footer__developed-by">
      <h2
        class="footer__text"
        :class="{'footer__text--dark' : (theme === 'dark')}"
        >
        Довгий Роман Олегович группа 201-321
      </h2>
    </section>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  props: [
    'theme',
  ],
};
</script>

<style>
  .footer {
    background-color: #F1F9FF;
    min-height: 5vh;
    transition: background-color 0.3s;
  }

  .footer--dark {
    background-color: #001930;
  }

  .footer__developed-by {
    max-width: 1200px;
    width: 100%;
    margin: 0 auto;
    padding: 15px 0;

    display: flex;
    justify-content: center;
  }

  .footer__text {
    color: #2699FB;
    transition: color 0.3s;
  }

  .footer__text--dark {
    color: #ffffff;
  }
</style>
