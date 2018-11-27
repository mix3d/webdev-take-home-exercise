<template>
    <header class="global-header" role="banner">
        <h1>Puppy image gallery</h1>
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
const quotes = [
    {
        text:"A dog will teach you unconditional love. If you can have that in your life, things won't be too bad.",
        author: "Robert Wagner"
    },
    {
        text:"Some quote for brevity",
        author: "ME"
    },
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
        // make sure the whole app has fully rendered!
        this.$nextTick(() => {
            interval = setInterval(this.nextQuote, 8000)
        })
    },
    beforeDestroy(){
        clearInterval(interval)
    },
}
</script>

<style lang="scss">
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
    transition: all 700ms ease-in-out;
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
