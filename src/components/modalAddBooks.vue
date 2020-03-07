<template>
    <transition name="modal-fade">
        <div class="modal-backdrop">
            <div class="modal">
                <header id="modalTitle">
                    <div class="header-close">
                        <button type="button" class="btn-close" @click="close">
                            <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="32" height="32" viewBox="0 0 172 172"
                                 style=" fill:#000000;"><g fill="none" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt" stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode: normal"><path d="M0,172v-172h172v172z" fill="none"></path><g fill="#da2f1e"><path d="M86,17.2c-37.9948,0 -68.8,30.8052 -68.8,68.8c0,37.9948 30.8052,68.8 68.8,68.8c37.9948,0 68.8,-30.8052 68.8,-68.8c0,-37.9948 -30.8052,-68.8 -68.8,-68.8zM112.9868,104.87987c2.24173,2.24173 2.24173,5.8652 0,8.10693c-1.118,1.118 -2.58573,1.67987 -4.05347,1.67987c-1.46773,0 -2.93547,-0.56187 -4.05347,-1.67987l-18.87987,-18.87987l-18.87987,18.87987c-1.118,1.118 -2.58573,1.67987 -4.05347,1.67987c-1.46773,0 -2.93547,-0.56187 -4.05347,-1.67987c-2.24173,-2.24173 -2.24173,-5.8652 0,-8.10693l18.87987,-18.87987l-18.87987,-18.87987c-2.24173,-2.24173 -2.24173,-5.8652 0,-8.10693c2.24173,-2.24173 5.8652,-2.24173 8.10693,0l18.87987,18.87987l18.87987,-18.87987c2.24173,-2.24173 5.8652,-2.24173 8.10693,0c2.24173,2.24173 2.24173,5.8652 0,8.10693l-18.87987,18.87987z"></path></g></g>
                            </svg>
                        </button>
                    </div>
                </header>
                <section class="modal-body" id="modalDescription">
                    <form id="app" @submit="checkForm">
                        <ion-item>
                            <ion-label position="floating">Title</ion-label>
                            <ion-input :value="this.title" @input="$v.title.$model=$event.target.value"></ion-input>
                        </ion-item>
                        <ion-item>
                            <ion-label position="floating">Autor</ion-label>
                            <ion-input :value="this.autor" @input="$v.autor.$model=$event.target.value"></ion-input>
                        </ion-item>
                        <ion-item>
                            <ion-label position="floating">Page count</ion-label>
                            <ion-input :value="this.page" type="number" @input="$v.page.$model=$event.target.value"></ion-input>
                        </ion-item>
                        <ion-item>
                            <ion-label position="floating">Picture link</ion-label>
                            <ion-input :value="this.link" type="url" @input="$v.link.$model=$event.target.value"></ion-input>
                        </ion-item>
                        <ion-item>
                            <ion-label position="stacked">Short description</ion-label>
                            <ion-textarea :value="this.description" @input="$v.description.$model=$event.target.value"></ion-textarea>
                        </ion-item>
                        <footer class="modal-footer">
                            <button type="submit" class="btn-green">
                                <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px"
                                     width="32" height="32"
                                     viewBox="0 0 172 172"
                                     style=" fill:#000000;"><g fill="none" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt" stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode: normal"><path d="M0,172v-172h172v172z" fill="none"></path><g fill="#61ae2e"><path d="M160.55856,83.46128l-79.12,-72.24c-1.00448,-0.92192 -2.46648,-1.1524 -3.70488,-0.60888c-1.24872,0.5504 -2.05368,1.78536 -2.05368,3.1476v27.52h-61.92c-1.90232,0 -3.44,1.53768 -3.44,3.44v82.56c0,1.90232 1.53768,3.44 3.44,3.44h61.92v27.52c0,1.36224 0.80496,2.5972 2.05368,3.1476c0.4472,0.19608 0.91504,0.2924 1.38632,0.2924c0.8428,0 1.67184,-0.3096 2.31856,-0.90128l79.12,-72.24c0.71552,-0.65016 1.12144,-1.57208 1.12144,-2.53872c0,-0.96664 -0.40592,-1.88856 -1.12144,-2.53872zM102.36408,67.60632l-32.68,37.84c-0.60544,0.70176 -1.47232,1.12832 -2.39424,1.1868c-0.07224,0.00344 -0.1376,0.00688 -0.20984,0.00688c-0.85312,0 -1.67872,-0.31648 -2.31512,-0.8944l-18.92,-17.2c-1.40352,-1.27968 -1.50672,-3.45376 -0.23048,-4.86072c1.28312,-1.40696 3.46064,-1.50672 4.86072,-0.23048l16.30904,14.82984l30.37176,-35.17056c1.24872,-1.4448 3.4228,-1.59616 4.8504,-0.35776c1.43792,1.24184 1.5996,3.41248 0.35776,4.8504z"></path></g></g>
                                </svg>
                            </button>
                        </footer>
                        <p v-if="errors.length">
                            <p v-for="error in errors">{{ error }}</p>
                        </p>
                    </form>
                </section>
            </div>
        </div>
    </transition>
</template>

<script>
    import { required } from 'vuelidate/lib/validators'

    export default {
        name: 'modalAddBooks',
        props:{
            books:Array
        },
        data(){
            return {
                store:this.books,
                errors: [],
                title: null,
                description:null,
                autor:null,
                link:null,
                page:null
            }
        },
        validations: {
            title: {
                required
            },
            description: {
                required
            },
            autor:{
                required
            },
            link:{
                required
            },
            page:{
                required
            }
        },
        methods: {
            close() {
                this.$emit('close');
                this.errors =[]
            },
            displayAndCheckError(errorArray, titleError) {
                if (errorArray.indexOf(titleError) === -1) {
                    errorArray.push(titleError);
                }
            },
            checkForm: function (e) {
                e.preventDefault();
                if (this.$v.title.required !==true) {
                    this.displayAndCheckError(this.errors,"Title required")
                }
                if (this.$v.autor.required !==true) {
                    this.displayAndCheckError(this.errors,"Author required")
                }
                if (this.$v.page.required !==true) {
                    this.displayAndCheckError(this.errors,"Page count required")
                }
                if (this.$v.link.required !==true) {
                    this.displayAndCheckError(this.errors,"Picture link required")
                }
                if (this.$v.description.required !==true) {
                    this.displayAndCheckError(this.errors,"Description required")
                }
                if (this.$v.title.required && this.$v.autor.required && this.$v.page.required && this.$v.link.required && this.$v.description.required) {
                    const objectName = {
                        title:this.title,
                        isbn : Math.floor((1 + Math.random()) * 0x10000),
                        pageCount:this.page,
                        thumbnailUrl:this.link,
                        shortDescription:this.description,
                        author:this.autor
                    };
                    this.books.unshift(objectName)
                    localStorage.setItem("storeBooks", JSON.stringify(this.books))
                    this.title = null
                    this.page = null
                    this.link = null
                    this.description = null
                    this.autor = null
                    this.close();
                }
            },
        },
    };
</script>
<style scoped lang="scss">
    p{
        color: red;
        margin-top: 10px;
        margin-bottom: 0;
        padding:0 13px;
        text-align: left;
    }
    ion-item{
        margin: 10px;
    }
    .header-close{
        text-align: right;
    }
    .modal-backdrop {
        position: fixed;
        top: 135px;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(0, 0, 0, 0.3);
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .modal {
        width: 100%;
        background: #FFFFFF;
        box-shadow: 2px 2px 20px 1px;
        z-index: 99;
        border-radius: 3px;
        display: flex;
        flex-direction: column;
    }
    .modal-footer {
        padding: 5px;
        display: flex;
    }
    .modal-footer {
        justify-content: flex-start;
    }
    .btn-close {
        border: none;
        padding: 5px;
        cursor: pointer;
        background-color: transparent;
        outline: none;
    }

    .btn-green {
        color: white;
        padding: 8px;
        background: transparent;
        outline: none;
    }
    .modal-fade-enter,
    .modal-fade-leave-active {
        opacity: 0;
    }

    .modal-fade-enter-active,
    .modal-fade-leave-active {
        transition: opacity .5s ease
    }
</style>
