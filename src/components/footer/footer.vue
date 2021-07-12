<template>
  <footer class="footer">
    <section class="footer__developed-by">
      <h2 class="footer__text">
        Довгий Роман Олегович группа 201-321
      </h2>
    </section>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
};
</script>

<style>
  .footer {
    background-color: #F1F9FF;
    min-height: 5vh;
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
  }
</style>
