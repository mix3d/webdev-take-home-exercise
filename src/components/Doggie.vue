<template>
    <div class="grid-item card">
        <div class="profile" :title="doggo.name" :aria-label="alt"
        :style="style">
        </div>
        <!-- <img :src="doggo.image" :title="doggo.name" :alt="alt"> -->
        <h3>{{doggo.name}}</h3>
        <table>
            <tr>
                <td>Breed:</td>
                <td>{{doggo.breed}}</td>
            </tr>
            <tr>
                <td>Likes:</td>
                <td>{{doggo.likes}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    props: [
        'doggo'
    ],
    computed:{
        alt() { return this.doggo.name + "'s Picture" },
        style() { return {'background-image': `url(${this.doggo.image})`} },
    }
}
</script>

<style lang='scss' scoped>
.profile {
    min-height: 200px;
    background-size: cover;
    // each dog is roughly centered in the shot
    background-position: 50% 50%;
}
h3{
    margin:0;
    padding: 6px;
    text-align: center;
    font-family: var(--font-bold);
}
td{
    padding: .5rem;
}
.card{
    background: var(--bg-light);
    // min-width: 200px;
}
</style>
