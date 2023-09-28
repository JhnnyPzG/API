<template>
  <v-app>
    <v-card>
      <v-app-bar absolute dark height="300%" shrink-on-scroll object-fit="cover"
        src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/d6862cb9-a6eb-46f4-8df9-411f38ffc20e/da18ugq-f031344b-1c87-4586-a4c7-5d71c308a435.jpg?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcL2Q2ODYyY2I5LWE2ZWItNDZmNC04ZGY5LTQxMWYzOGZmYzIwZVwvZGExOHVncS1mMDMxMzQ0Yi0xYzg3LTQ1ODYtYTRjNy01ZDcxYzMwOGE0MzUuanBnIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.bk_lz2tZx3GqPcWInNeT9S-nHdjnmUDfXClIQCTcd8Q">

        <v-btn @click="toggleSearch" icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-text-field v-model="searchTerm" label="Buscar personaje" hide-details solo-inverted class="custom-search-field"
          @input="searchCharacters" v-if="showSearch" filled flat></v-text-field>

      </v-app-bar>

      <Lista :characters="characters" :filteredCharacters="filteredCharacters" />

    </v-card>

    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>

    <v-footer>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
import axios from 'axios';

export default {
  name: 'DefaultLayout',

  data() {
    return {
      title: 'MARVEL',
      searchTerm: '',
      showSearch: false,
      characters: [],
      filteredCharacters: [],
    };
  },

  methods: {
    async searchCharacters() {
      try {
        if (this.searchTerm !== '') {
          const response = await axios.get(
            `https://gateway.marvel.com/v1/public/characters`,
            {
              params: {
                ts: 1,
                apikey: '457e0666067e7294e366a7f09b3dfc13',
                hash: '98c6c135471dc731a99d4bc5824c9ab9',
                limit: 100,
                nameStartsWith: this.searchTerm,
              },
            }
          );

          this.filteredCharacters = response.data.data.results;
        } else {
          this.filteredCharacters = this.characters;
        }
      } catch (error) {
        console.error(error);
      }
    },


    toggleSearch() {
      this.showSearch = !this.showSearch;
      if (!this.showSearch) {
        this.searchTerm = '';
      }
    },
  },

  watch: {
    searchTerm(newTerm, oldTerm) {
      if (newTerm === '') {
        this.filteredCharacters = this.characters;
      }
    },
  },

  beforeCreate() {
    axios.get('https://gateway.marvel.com/v1/public/characters?ts=1&apikey=457e0666067e7294e366a7f09b3dfc13&hash=98c6c135471dc731a99d4bc5824c9ab9&limit=100')
      .then((response) => {
        this.characters = response.data.data.results;
        this.filteredCharacters = this.characters;
        console.log(response.data.data.results);
      })
      .catch((error) => console.error(error));
  },
};
</script>

<style scoped>
.custom-search-field {
  max-width: 300px;
  margin: 0 auto;
  background-color: rgba(0, 0, 0, 0.5);
  border-radius: 4px;
}

.custom-search-field input {
  color: white;
}

.custom-search-field .v-icon {
  color: white;
}
</style>
