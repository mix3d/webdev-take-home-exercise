<template>
    <div class="modal-body">
        <h1>{{doggo.name}}</h1>
        <div :title="doggo.name" :aria-label="alt" class="profile" :style="style"></div>

        <label>Breed:</label>
        <p>{{doggo.breed}}</p>
        <label>Likes:</label>
        <p>{{doggo.likes}}</p>
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

<style lang="scss" scoped>
.modal-body{
    display:flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
    padding: 1rem;
    @media (min-width: 680px) {
        padding:1rem 2rem 2rem;
    }
}
h1{
    text-align: center;
    font-size:2em;
}
.profile {
    min-height: 500px;
    background-size: contain;
    background-repeat: no-repeat;
    flex-grow: 1;
}
label{
    font-weight: 700;
    color: var(--theme);
    margin-top: 1em;
}
p{
    margin: 0
}
label, p{
    font-size: 18px;
}

</style>
