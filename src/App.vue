<template>
  <div id="app">
    <div class="container">
      <img src="./assets/images/dogasana.svg" height="30px">
      <a-header></a-header>
      <article>
        <doggie-grid :doggos="doggos"></doggie-grid>
      </article>
    </div>
    <a-footer></a-footer>
  </div>
</template>

<script>
// Can't use header/footer since they're reserved element names. A for Asana.
import aHeader from './components/Header.vue'
import aFooter from './components/Footer.vue'
import DoggieGrid from './components/DoggieGrid.vue'

// Temp Data sources
import {dogs} from './assets/data/dogs.json'
import names from './assets/data/names.json'
import breeds from './assets/data/breeds.json'
import likes from './assets/data/likes.json'

// Pretend this data came from an Ajax service
dogs.forEach((dog, index) => {
  dog.name = names[Math.floor(Math.random() * names.length)]
  dog.breed = breeds[Math.floor(Math.random() * breeds.length)]
  dog.likes = likes[Math.floor(Math.random() * likes.length)]
  dog.saved = false
  dog.id = index
})

console.log(dogs)

export default {
  name: 'app',
  data () {
    return {
      doggos: dogs
    }
  },
  computed:{
    savedDoggos(){
      return this.doggos.filter(dog => dog.saved);
    }
  },
  components:{
    aHeader,
    aFooter,
    DoggieGrid,
  },
}
</script>

<style lang="scss">
$width-small: 680px;

body:before {
  content:'';
  width: 100%;
  position: absolute;
  top:0;
  background: url('./assets/images/bons-and-foot-prints-pattern-background_1374-18.jpg') repeat;
  background-size: 169px 169px; // half-size for better size and 2x crispness
  height: 200px;
  z-index: -1;
}

#app {
  display:flex;
  flex-direction: column;
  align-items: center;
}

.container{
  background: white;
  padding: 1rem;
  width:100%;

  @media (min-width: $width-small) {
    max-width: 1000px;
    border-radius: var(--radius);
    box-shadow: var(--soft-shadow);
    margin: 80px 26px 26px;
    width:calc(100% - 52px);
  }
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

</style>
