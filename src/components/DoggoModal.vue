<template>
    <div class="modal-body">
        <h1>
            <paw v-if="doggo.saved" style="width: 30px; vertical-align: baseline; color: var(--accent);"></paw>
            {{doggo.name}}
        </h1>
        <div :title="doggo.name" :aria-label="alt" class="profile" :style="style"></div>
        <div>
            <label>Breed:</label>
            <p>{{doggo.breed}}</p>
            <label>Likes:</label>
            <p>{{doggo.likes}}</p>
        </div>

        <button @click="favoriteDoggo">
            <paw style="width: 20px;"></paw>
            {{btnText}}
        </button>
    </div>
</template>

<script>
import Paw from "./Paw"

export default {
    props: [
        'doggo'
    ],
    computed:{
        alt() { return this.doggo.name + "'s Picture" },
        style() { return {'background-image': `url(${this.doggo.image})`} },
        btnText(){ return `${this.doggo.saved ? 'Unfavorite' : 'Favorite'} ${this.doggo.name}` }
    },
    methods:{
        favoriteDoggo(){
            // This is a known bad pattern, Vuex / Flux state should be used instead of child-modification of objects... side-effects are bad.
            // But this is a quick takehome assignment for Asana, so shortcut made.
            this.doggo.saved = !this.doggo.saved;
            // this.$emit('favoriteDoggo',doggo)
        },
    },
    components:{
        Paw
    }
}
</script>

<style lang="scss" scoped>
$width-small: 680px;

.modal-body{
    display:flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
    padding: 1rem;
    @media (min-width: $width-small) {
        padding:1rem 2rem 2rem;
    }
    font-size: 18px;
}
h1{
    text-align: center;
    font-size:2em;
}
.profile {
    min-height: 300px;
    background-size: contain;
    background-repeat: no-repeat;
    flex-grow: 1;
}
label{
    display: block;
    font-weight: 700;
    color: var(--theme);
    margin-top: 1em;
    + p{
        margin-top: 0;
    }
}
// p{
//     margin: 0
// }

button{
    background: var(--theme);
    color: white;
    border:none;
    border-radius: 4px;
    padding: .5rem 1rem;
    align-self:center;
    font-size: inherit;
    letter-spacing: .05em;
    font-family: var(--font-bold);
    box-shadow: var(--small-shadow);
    &:hover{
        background: var(--bg-dark)
    }
    &:active{
        background: var(--accent)
    }
}
svg{
    display: inline-block;
    padding-top:2px;
    vertical-align:bottom;
}

</style>
