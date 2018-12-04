<template>
<div>
    <div class="grid">
        <doggie v-for="doggo in doggos" :key="doggo.id"
        @click.native="selectDoggo(doggo)"
        :doggo="doggo">
        </doggie>
    </div>
    <pagination></pagination>
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
import Pagination from './Pagination.vue'

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
        Pagination,
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
</style>
