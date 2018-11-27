<template>
    <figure class="grid-item">
        <img :src="doggo.image" :title="doggo.name" :alt="alt">
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
    </figure>
</template>

<script>
export default {
    props: [
        'doggo'
    ],
    computed:{
        alt() { return this.doggo.name + "'s Picture" },
    }
}
</script>

<style lang='scss' scoped>
img {
    max-width: 200px;
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
</style>
