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
    :startDrag="startDrag"
    :onDrop="onDrop"
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
          date: '2021-07-13T01:41:59.164Z',
        },
        {
          id: '2',
          description: 'Изучить Vue',
          priority: 2,
          type: ColumnType.WORKING,
          date: '2021-07-13T01:41:59.164Z',
        },
        {
          id: '3',
          description: 'Изучить Vue',
          priority: 3,
          type: ColumnType.DONE,
          date: '2021-07-13T01:41:59.164Z',
        },
        {
          id: '4',
          description: 'Изучить Vue',
          priority: 4,
          type: ColumnType.WORKING,
          date: '2021-07-13T01:41:59.164Z',
        },
        {
          id: '5',
          description: 'Изучить Vue',
          priority: 5,
          type: ColumnType.PLANNED,
          date: '2021-07-13T01:41:59.164Z',
        },
      ],
    };
  },
  methods: {
    handleModal() {
      const oldState = this.STATE.isModalOpen;
      if (oldState) {
        this.flushCurrent();
      }
      this.STATE.isModalOpen = !oldState;
    },
    workWithTask(descriptionLocal, priorityLocal, idLocal = '') {
      if (idLocal !== '') {
        const oldCard = this.CARDS.find((card) => card.id === idLocal);
        const newData = {
          description: descriptionLocal,
          priority: priorityLocal,
        };
        Object.assign(oldCard, newData);
      } else {
        let oldMaxId;

        if (!idLocal) {
          this.CARDS.sort((a, b) => a.id - b.id);
          oldMaxId = this.CARDS[this.CARDS.length - 1].id;
          console.log(oldMaxId);
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
        case ColumnType.DONE:
          this.deleteTask(id);
          return;
        default:
          break;
      }
      Object.assign(oldCard, newData);
    },
    changeTheme() {
      this.STATE.theme = this.STATE.theme === 'light' ? 'dark' : 'light';
    },
    startDrag(event, item) {
      // eslint-disable-next-line no-param-reassign
      event.dataTransfer.dropEffect = 'move';
      // eslint-disable-next-line no-param-reassign
      event.dataTransfer.effectAllowed = 'move';
      event.dataTransfer.setData('id', item.id);
    },
    onDrop(event, columnType) {
      const cardId = event.dataTransfer.getData('id');
      const card = this.CARDS.find((cardLocal) => cardLocal.id === cardId);
      card.type = columnType;
    },
    flushCurrent() {
      this.STATE.selectedCard = {
        id: '',
        description: '',
        priority: '',
        type: ColumnType.PLANNED,
        date: '',
      };
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
