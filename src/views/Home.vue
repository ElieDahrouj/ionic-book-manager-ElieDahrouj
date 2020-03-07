<template>
  <div class="ion-page">
    <ion-header>
      <headBook></headBook>
    </ion-header>
    <ion-content>
      <books :allBooks="this.bookStore"></books>
    </ion-content>
    <ion-fab vertical="bottom" horizontal="end" slot="fixed">
      <ion-fab-button>
        <ion-icon @click="showModal" name="add"></ion-icon>
      </ion-fab-button>
    </ion-fab>
    <modal :books="this.bookStore" v-show="isModalVisible" @close="closeModal"/>
  </div>
</template>

<script>
    import headBook from '@/components/headerbook.vue'
    import dataBooks from '@/assets/data/dataBooks.json'
    import books from '@/components/books.vue'
    import modal from '@/components/modalAddBooks.vue'
    export default {
        name: 'Home',
        components: {
            headBook,
            books,
            modal
        },
        data(){
          return{
              bookStore : dataBooks,
              isModalVisible: false,
          }
        },
        mounted(){
            if (localStorage.getItem("storeBooks")){
                this.bookStore = JSON.parse(localStorage.getItem("storeBooks"))
            }
        },
        methods: {
            showModal() {
                this.isModalVisible = true;
            },
            closeModal() {
                this.isModalVisible = false;
            }
        }
    }
</script>
<style lang="scss">
  .modal-fade-enter,
  .modal-fade-leave-active {
    opacity: 0;
  }

  .modal-fade-enter-active,
  .modal-fade-leave-active {
    transition: opacity .5s ease
  }
</style>
