<template>
  <section>
    <div class="container-row">
      <div id="liste" class="container-wrap">
        <Character v-for="character in filteredCharacters" :key="character.id" :character="character" />
      </div>
    </div>
  </section>
</template>

<script>
import Character from '../components/Personaje'

export default {
  name: 'Lista',

  components: {
    Character
  },

  props: {
    characters: {
      type: Array,
      default: () => [],
    },
    filteredCharacters: {
      type: Array,
      default: () => [],
    },
  },
}
</script>

<style>
.container-row {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

.container-wrap {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: flex-start;
}

#liste {
  width: 1050px;
  height: auto;
  margin: 40px;
  margin-top: 300px;
  margin-bottom: 20px; /* Reducido de 40px a 20px */
}
</style>
