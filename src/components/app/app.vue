<template>
  <Header/>
  <Main/>
  <Footer/>
  <Modal/>
</template>

<script>
import Header from '../header/header.vue';
import Main from '../main/main.vue';
import Footer from '../footer/footer.vue';
import Modal from '../modal/modal.vue';

export default {
  name: 'App',
  components: {
    Header,
    Main,
    Footer,
    Modal,
  },
};
</script>

<style>
  *,
  *::before,
  *::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  html {
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    font-size: 62.5%;
  }

  #app {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    position: relative;
  }

  .visually-hidden {
    position: absolute;
    width: 1px;
    height: 1px;
    margin: -1px;
    padding: 0;
    overflow: hidden;
    border: 0;
    clip: rect(0 0 0 0)
  }
</style>
