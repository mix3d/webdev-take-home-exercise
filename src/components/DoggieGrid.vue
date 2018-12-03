<template>
<div>
    <div class="grid">
        <doggie v-for="doggo in doggos" :key="doggo.id"
        @click.native="selectDoggo(doggo)"
        :doggo="doggo">
        </doggie>
    </div>
    <div class="pagination">
        <img src="left-chevron.svg" alt="">
        <div class="pages">
            1/1
        </div>
        <img src="right-chevron.svg" alt="">
    </div>
    <modal v-model="showModal">
        <big-doggie v-if="selectedDoggo" :doggo="selectedDoggo">
        </big-doggie>
    </modal>
</div>
</template>

<script>
import Modal from './modals/Modal.vue'
import BigDoggie from './DoggoModal.vue'
import Doggie from './Doggie.vue'

export default {
    props:[
        'doggos'
    ],
    data() {
        return {
            selectedDoggo: null,
            showModal: false,
        }
    },
    methods: {
        selectDoggo(doggo){
            console.log("selected",doggo)
            this.selectedDoggo = doggo
            this.showModal = true
        }
    },
    components:{
        Doggie,
        BigDoggie,
        Modal,
    }
}
</script>

<style lang="scss">
.grid {
    display: grid;
    // Create a grid with min-width columns of 200px, stretching to fit the container
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    grid-gap: 1rem;
}
.pagination{
    display: flex;
    padding: 0 4rem;
    margin-top: 1rem;
    .pages{
        flex-grow:1;
        text-align: center;
    }
    img{
        border-radius: 50%;
        border: none;
        float: right;
        padding: 0.75rem;
        box-shadow: var(--soft-shadow)
    }
}
</style>
