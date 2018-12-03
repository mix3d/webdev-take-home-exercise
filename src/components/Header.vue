<template>
    <header class="global-header" role="banner">
        <h1>Puppy image gallery</h1>
        <!-- transition group allows for simple switching between elements; in this case, quotes -->
        <transition-group name="slide" tag="div" class="slider">
            <div :key="quote.author">
            <blockquote class="header-quote"  @click="nextQuote">
                <p>{{quote.text}}</p>
                <cite>&mdash;{{quote.author}}</cite>
            </blockquote>
            </div>
        </transition-group>
    </header>
</template>

<script>
// TODO: Fill with more doggo quotes
const quotes = [
    {
        text:"A dog will teach you unconditional love. If you can have that in your life, things won't be too bad.",
        author: "Robert Wagner"
    },
    {
        text: "A dog is the only thing on earth that loves you more than you love yourself.",
        author: "Josh Billings"
    },
    {
        text: "Before you get a dog, you can't quite imagine what living with one might be like; afterward, you can't imagine living any other way.",
        author: "Caroline Knapp"
    },
    {
        text: "My fashion philosophy is, if you're not covered in dog hair, your life is empty.",
        author: "Elayne Boosler"
    }

]
let index = 0;
let interval;
export default {
    data() {
        return {
            quote: quotes[index]
        }
    },
    methods: {
        nextQuote(){
            this.quote = quotes[index++]
            if(index >= quotes.length){
                index = 0;
            }
        }
    },
    mounted(){
        // Removed auto quote movement because it interfered with performance on the rest of the page
        // Either multiple running CSS transitions are a bad idea, or Vue's transition group has significant performance issues.
        // make sure the whole app has fully rendered!
        // this.$nextTick(() => {
        //     interval = setInterval(this.nextQuote, 8000)
        // })
    },
    beforeDestroy(){
        clearInterval(interval)
    },
}
</script>

<style lang="scss">

cite{
    color: var(--bg-dark);
}

.slider{
    position:relative;
    /* text-align: center; */
    overflow: hidden;
    height: 120px;
    >div{
        position: absolute;
        top:0;
        left:0;
        width: 100%;
    }
}

.slide-enter-active,
.slide-leave-active {
    transition: all 300ms ease-in-out;
}

.slide-enter, .slide-leave-active{
    opacity: 0;
}

.slide-enter{
    transform: translateX(100px);
}
.slide-leave-active {
    transform: translateX(-100px);
}

</style>
