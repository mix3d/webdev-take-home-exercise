<template>
<div>
    <div class="grid">
        <doggie v-for="doggo in doggos" :key="doggo.id"
        @click="selectDoggo(doggo)"
        :doggo="doggo">
        </doggie>
    </div>
    <modal :shown="showModal" :data="selectedDoggo" :component="DoggoModal"></modal>
</div>
</template>

<script>
import Modal from './modals/Modal.vue'
import DoggoModal from './DoggoModal.vue'
import Doggie from './Doggie.vue'

export default {
    props:[
        'doggos'
    ],
    data() {
        return {
            selectedDoggo: null,
            DoggoModal,
            showModal: false,
        }
    },
    methods: {
        selectDoggo(doggo){
            this.selectedDoggo = doggo
            this.showModal = true
        }
    },
    components:{
        Doggie,
        Modal,
    }
}
</script>

<style lang="scss">
.grid {
    display: grid;
    // Create a grid with min-width columns of 300px, stretching to fit the container
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    grid-gap: 1rem;
}
</style>
