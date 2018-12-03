<template>
    <div class="grid-item card hover">
        <paw v-if="doggo.saved" class="jellybean" ></paw>
        <div class="profile" :title="doggo.name" :aria-label="alt"
        :style="style">
        </div>
        <!-- <img :src="doggo.image" :title="doggo.name" :alt="alt"> -->
        <h3>{{doggo.name}}</h3>
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
    },
    components:{
        Paw,
    }
}
</script>

<style lang='scss' scoped>
.grid-item {
    position: relative;
}
h3{
    margin:0;
    padding: 6px;
    text-align: center;
}
.jellybean{
    width: 26px; height: 26px;
    position: absolute;
    top:.5rem; right: .5rem;
    color: var(--accent);
    // potentially unsupported in some browsers, but makes the paw pop over busy images
    filter: drop-shadow( 0 2px 6px rgba(0,0,0,.4) );
}
</style>
