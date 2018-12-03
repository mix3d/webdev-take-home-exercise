<template>
    <div class="grid-item card hover" @click="handleClick">
        <div class="profile" :title="doggo.name" :aria-label="alt"
        :style="style">
        </div>
        <!-- <img :src="doggo.image" :title="doggo.name" :alt="alt"> -->
        <h3>{{doggo.name}}</h3>
        <!-- <table>
            <tr>
                <td>Breed:</td>
                <td>{{doggo.breed}}</td>
            </tr>
            <tr>
                <td>Likes:</td>
                <td>{{doggo.likes}}</td>
            </tr>
        </table> -->
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
    },
    methods:{
        handleClick(){
            console.log("doggie clicked",this.doggo)
        }
    }
}
</script>

<style lang='scss' scoped>
h3{
    margin:0;
    padding: 6px;
    text-align: center;
}
td{
    padding: .5rem;
}
</style>
