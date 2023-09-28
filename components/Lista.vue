<template>
  <section>
    <div class="container-row">
      <div id="liste" class="container-wrap">
        <Character
          v-for="character in filteredCharacters"
          :key="character.id"
          :character="character"
          v-if="characterHasAnyInfo(character)"
        />
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
      default: () => []
    },
    filteredCharacters: {
      type: Array,
      default: () => []
    }
  },

  methods: {
    characterHasAnyInfo(character) {
      return (
        character.name ||
        character.description ||
        (character.thumbnail &&
          character.thumbnail.path &&
          character.thumbnail.extension) ||
        (character.comics && character.comics.available > 0) ||
        (character.series && character.series.available > 0) ||
        (character.events && character.events.available > 0) ||
        (character.stories && character.stories.available > 0)
      );
    }
  }
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
}
</style>
