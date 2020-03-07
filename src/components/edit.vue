<template>
    <transition name="modal-fade">
        <div>
            <div>
                <header>
                    <div class="header-close">
                        <button type="button" class="btn-close" @click="close">
                            <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="32" height="32" viewBox="0 0 172 172"
                                 style=" fill:#000000;"><g fill="none" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt" stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode: normal"><path d="M0,172v-172h172v172z" fill="none"></path><g fill="#da2f1e"><path d="M86,17.2c-37.9948,0 -68.8,30.8052 -68.8,68.8c0,37.9948 30.8052,68.8 68.8,68.8c37.9948,0 68.8,-30.8052 68.8,-68.8c0,-37.9948 -30.8052,-68.8 -68.8,-68.8zM112.9868,104.87987c2.24173,2.24173 2.24173,5.8652 0,8.10693c-1.118,1.118 -2.58573,1.67987 -4.05347,1.67987c-1.46773,0 -2.93547,-0.56187 -4.05347,-1.67987l-18.87987,-18.87987l-18.87987,18.87987c-1.118,1.118 -2.58573,1.67987 -4.05347,1.67987c-1.46773,0 -2.93547,-0.56187 -4.05347,-1.67987c-2.24173,-2.24173 -2.24173,-5.8652 0,-8.10693l18.87987,-18.87987l-18.87987,-18.87987c-2.24173,-2.24173 -2.24173,-5.8652 0,-8.10693c2.24173,-2.24173 5.8652,-2.24173 8.10693,0l18.87987,18.87987l18.87987,-18.87987c2.24173,-2.24173 5.8652,-2.24173 8.10693,0c2.24173,2.24173 2.24173,5.8652 0,8.10693l-18.87987,18.87987z"></path></g></g>
                            </svg>
                        </button>
                    </div>
                </header>
                <section>
                    <ion-item>
                        <ion-label position="floating">Title</ion-label>
                        <ion-input :value="singleBook.title" @input="$v.singleBook.title.$model=$event.target.value" type="text"></ion-input>
                    </ion-item>
                    <ion-item>
                        <ion-label position="floating">Autor</ion-label>
                        <ion-input :value="singleBook.author" @input="$v.singleBook.author.$model=$event.target.value" type="text"></ion-input>
                    </ion-item>
                    <ion-item>
                        <ion-label position="floating">Page count</ion-label>
                        <ion-input :value="singleBook.pageCount" type="number" @input="$v.singleBook.pageCount.$model=$event.target.value"></ion-input>
                    </ion-item>
                    <ion-item>
                        <ion-label position="floating">Picture link</ion-label>
                        <ion-input :value="singleBook.thumbnailUrl" type="url" @input="$v.singleBook.thumbnailUrl.$model=$event.target.value"></ion-input>
                    </ion-item>
                    <ion-item>
                        <ion-label position="stacked">Short description</ion-label>
                        <ion-textarea :value="singleBook.shortDescription" @input="$v.singleBook.shortDescription.$model=$event.target.value"></ion-textarea>
                    </ion-item>
                    <footer>
                        <button class="btn-edit" @click="update" type="button" >Editez
                            <ion-icon name="create"></ion-icon>
                        </button>
                        <p>{{error}}</p>
                    </footer>
                </section>
            </div>
        </div>
    </transition>
</template>

<script>
    import { required } from 'vuelidate/lib/validators'
    export default {
        name: 'edition',
        props:{
            singleBook:Object,
            editionBooks : Array
        },
        validations: {
            singleBook: {
                title: {
                    required
                },
                shortDescription: {
                    required
                },
                author:{
                    required
                },
                thumbnailUrl:{
                    required
                },
                pageCount:{
                    required
                }
            }
        },
        data(){
            return {
                error:null
            }
        },
        methods:{
            close() {
                this.$emit('close');
            },
            update () {
                if (!this.$v.singleBook.$invalid) {
                    localStorage.setItem("storeBooks",JSON.stringify(this.editionBooks))
                    this.close()
                }
                else {
                    this.error = "Tous les champs sont obligatoire"
                }
            }
        },
    };
</script>
<style scoped lang="scss">
    .btn-edit {
        outline: none;
        padding: 7px;
        color: #ffbd42;
        background-color: transparent;
        border: 1px solid #ffbd42;
        border-radius: 3px;
        margin-top: 10px;
    }
    footer{
        padding-left: 15px;
    }
    .header-close{
        text-align: right;
    }
    .btn-close{
        background-color: transparent;
        outline: none;
    }
    p{
        color: red;
        margin: 5px 0;
    }
</style>


