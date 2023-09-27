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
    axios.get('https://gateway.marvel.com/v1/public/characters?apikey=64f8a4a135a118c96d90eeedb37d61c8&hash=64f8a4a135a118c96d90eeedb37d61c8')
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
