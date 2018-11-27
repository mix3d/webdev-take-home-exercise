<template>
<div>
    <div class="grid">
        <doggie v-for="doggo in doggos" :key="doggo.id"
        @click="selectDoggo"
        :doggo="doggo">
        </doggie>
    </div>
    <modal :data="selectedDoggo" :component="DoggoModal"></modal>
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
        }
    },
    methods: {
    },
    components:{
        Doggie,
        Modal,
    }
}
</script>

<style>
</style>
