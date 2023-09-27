<template>
<section>
    <div class="container-row">
      <div id="liste" class="container-wrap" >
        <Character v-for="character in characters" :key="character.id" :character="character"/>
      </div>
    </div>
   
  </section>
</template>

<script>
import axios from 'axios'
import Character from '../components/Personaje'

export default {
  name: 'Lista',

  components: {
    Character
  },

  data() {
    return {
      characters:[]
    }
  },

  methods:{
    
      },

  beforeCreate() {
    axios.get('https://gateway.marvel.com/v1/public/characters?ts=1&apikey=457e0666067e7294e366a7f09b3dfc13&hash=98c6c135471dc731a99d4bc5824c9ab9&limit=100')


      .then((response) => {this.characters = response.data.data.results;
              console.log(response.data.data.results)})
      .catch( (error) => console.error(error));
  }
}
</script>

<style>
.container-row {
  display : flex;
  flex-direction: row;
  justify-content: space-around;
}

.container-wrap {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: flex-start;
}

#liste{
  width: 1050px;
  height: auto;
  margin: 40px;
}

</style>
