<template>
  <Header
    :changeTheme="changeTheme"
    :theme="STATE.theme"
  />
  <Main
    :cards="CARDS"
    :handleModal="handleModal"
    :handleChangeCard="handleChangeCard"
    :deleteTask="deleteTask"
    :moveRight="moveRight"
    :moveLeft="moveLeft"
    :theme="STATE.theme"
    />
  <Footer
    :theme="STATE.theme"
  />
  <Modal
    v-if="STATE.isModalOpen"
    :handleModal="handleModal"
    :workWithTask="workWithTask"
    :descriptionForChange="STATE.selectedCard.description"
    :priorityForChange="STATE.selectedCard.priority"
    :idForChange="STATE.selectedCard.id"/>
</template>

<script>
import { ColumnType } from '../../utils/const';
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
  data() {
    return {
      STATE: {
        theme: 'light',
        isModalOpen: false,
        selectedCard: {
          id: '',
          description: '',
          priority: '',
          type: ColumnType.PLANNED,
          date: '',
        },
      },
      CARDS: [
        {
          id: '1',
          description: 'Изучить Vue',
          priority: 1,
          type: ColumnType.PLANNED,
          date: 'Mon Jul 12 2021 23:28:39 GMT+0300 (Moscow Standard Time)',
        },
        {
          id: '2',
          description: 'Изучить Vue',
          priority: 2,
          type: ColumnType.WORKING,
          date: 'Mon Jul 11 2021 23:28:39 GMT+0300 (Moscow Standard Time)',
        },
        {
          id: '3',
          description: 'Изучить Vue',
          priority: 3,
          type: ColumnType.DONE,
          date: 'Mon Jul 10 2021 23:28:39 GMT+0300 (Moscow Standard Time)',
        },
        {
          id: '4',
          description: 'Изучить Vue',
          priority: 4,
          type: ColumnType.WORKING,
          date: 'Mon Jul 5 2021 23:28:39 GMT+0300 (Moscow Standard Time)',
        },
        {
          id: '5',
          description: 'Изучить Vue',
          priority: 5,
          type: ColumnType.PLANNED,
          date: 'Mon Jul 1 2021 23:28:39 GMT+0300 (Moscow Standard Time)',
        },
      ],
    };
  },
  methods: {
    handleModal() {
      const oldState = this.STATE.isModalOpen;
      this.STATE.isModalOpen = !oldState;
    },
    workWithTask(descriptionLocal, priorityLocal, idLocal = '') {
      if (idLocal) {
        const oldCard = this.CARDS.find((card) => card.id === idLocal);
        const newData = {
          description: descriptionLocal,
          priority: priorityLocal,
        };
        Object.assign(oldCard, newData);
      } else {
        let oldMaxId;

        if (idLocal) {
          this.CARDS.sort((a, b) => a.id - b.id);
          oldMaxId = this.CARDS[this.CARDS.length - 1].id;
        } else {
          oldMaxId = 0;
        }
        const newId = Number(oldMaxId) + 1;
        const newDate = new Date();
        this.CARDS.push({
          id: `${newId}`,
          description: descriptionLocal,
          priority: priorityLocal,
          type: ColumnType.PLANNED,
          date: newDate,
        });
      }
    },
    deleteTask(id) {
      const removedIndex = this.CARDS.findIndex((card) => card.id === id);

      this.CARDS.splice(removedIndex, 1);
      console.log(this.CARDS);
    },
    handleChangeCard(id) {
      this.STATE.selectedCard = Object.assign(this.CARDS.find((card) => card.id === id));
      this.handleModal();
    },
    moveLeft(id) {
      const oldCard = this.CARDS.find((card) => card.id === id);
      let newData = {};
      switch (oldCard.type) {
        case ColumnType.WORKING:
          newData = {
            type: ColumnType.PLANNED,
          };
          break;
        case ColumnType.DONE:
          newData = {
            type: ColumnType.WORKING,
          };
          break;
        default:
          break;
      }
      Object.assign(oldCard, newData);
    },
    moveRight(id) {
      const oldCard = this.CARDS.find((card) => card.id === id);
      let newData = {};
      switch (oldCard.type) {
        case ColumnType.PLANNED:
          newData = {
            type: ColumnType.WORKING,
          };
          break;
        case ColumnType.WORKING:
          newData = {
            type: ColumnType.DONE,
          };
          break;
        default:
          break;
      }
      Object.assign(oldCard, newData);
    },
    changeTheme() {
      this.STATE.theme = this.STATE.theme === 'light' ? 'dark' : 'light';
      console.log(this.STATE.theme);
    },
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
