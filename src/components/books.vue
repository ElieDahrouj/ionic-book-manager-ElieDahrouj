<template>
    <div>
        <ion-list>
            <ion-item v-for="(allBook) in allBooks" v-bind:key="allBook.text">
                <ion-thumbnail slot="start">
                    <img :src="allBook.thumbnailUrl">
                </ion-thumbnail>
                <ion-label>
                    <h2>
                        {{allBook.title}}
                    </h2>
                    <h4>
                        {{allBook.author}}
                    </h4>
                    <p>
                        {{allBook.shortDescription}}
                    </p>
                    <ion-button @click="presentActionSheet(allBook.isbn)">Action</ion-button>
                    <edition  @close="closeModal" :singleBook="allBook" :editionBooks="allBooks"  v-if="editionModal === allBook.isbn && isModalVisible"></edition>
                </ion-label>
            </ion-item>
        </ion-list>
    </div>
</template>

<script>
    import edition from '@/components/edit.vue'
    import modal from '@/components/modalAddBooks.vue'
    export default {
        name: 'books',
        props:{
            allBooks : Array
        },
        components:{
            edition,
            modal
        },
        data(){
          return {
              editionModal:false,
              isModalVisible: false,
          }
        },
        methods: {
            closeModal() {
                this.isModalVisible = false;
            },
            editmodalVisible(idbn){
                    this.editionModal = idbn
            },
            presentActionSheet(id) {
                return this.$ionic.actionSheetController
                    .create({
                        buttons: [
                            {
                                text: 'Delete',
                                role: 'destructive',
                                icon: 'trash',
                                handler: () => {
                                    console.log(id)
                                    this.allBooks.forEach(book => {
                                        if (book.isbn === id) {
                                            this.allBooks.splice(this.allBooks.indexOf(book), 1)
                                            localStorage.setItem("storeBooks", JSON.stringify(this.allBooks))
                                        }
                                    })
                                },
                            },
                            {
                                text: 'Edition',
                                icon: 'heart',
                                handler: () => {
                                    this.editmodalVisible(id)
                                    this.isModalVisible = true
                                },
                            },
                            {
                                text: 'Cancel',
                                icon: 'close',
                                role: 'cancel',
                            },
                        ],
                    })
                    .then(a => a.present())
            },
        },
    }
</script>
<style scoped lang="scss">
    .modal-fade-enter,
    .modal-fade-leave-active {
        opacity: 0;
    }

    .modal-fade-enter-active,
    .modal-fade-leave-active {
        transition: opacity .5s ease
    }
</style>