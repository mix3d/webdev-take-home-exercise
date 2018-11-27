<template>
  <div id="app">
    <div class="container">
      <a-header></a-header>
      <content>
      </content>
      <a-footer></a-footer>
    </div>
  </div>
</template>

<script>
// Can't use header/footer since they're reserved element names. A for Asana.
import aHeader from './components/Header.vue'
import aFooter from './components/Footer.vue'

// Temp Data sources
import {dogs} from './assets/data/dogs.json'
import names from './assets/data/names.json'
import breeds from './assets/data/breeds.json'
import likes from './assets/data/likes.json'

// Pretend this data came from an Ajax service
dogs.forEach(dog => {
  dog.name = names[Math.floor(Math.random() * names.length)]
  dog.breed = breeds[Math.floor(Math.random() * breeds.length)]
  dog.likes = likes[Math.floor(Math.random() * likes.length)]
  dog.saved = false
})

console.log(dogs)

export default {
  name: 'app',
  data () {
    return {
      doggos: dogs
    }
  },
  components:{
    aHeader,
    aFooter,
  }
}
</script>

<style lang="scss">
body:before{
  content:'';
  width: 100%;
  position: absolute;
  top:0;
  background: url('./assets/images/bons-and-foot-prints-pattern-background_1374-18.jpg') repeat;
  background-size: 169px 169px;
  height: 200px;
  z-index: -1;
}

#app {
  padding: 104px 26px 26px;
}

.container{
  max-width: 900px;
  background: white;
  border-radius: var(--radius);
  box-shadow: var(--soft-shadow);
  margin: 0 auto;
  padding: 1rem;

  @media (min-width: 1024px) {
    
  }
  @media (min-width: 1224px) {
    
  }
}

h1, h2 {
  font-weight: normal;
  margin: 0 .5rem;
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
