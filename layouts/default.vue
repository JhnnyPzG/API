<template>
  <v-app>
    <v-card>
      <v-app-bar
        absolute
        dark
        height="220px"
        shrink-on-scroll
        src="https://images.squarespace-cdn.com/content/v1/5aff290555b02c20b1addd50/1546875850690-VX6V3C57ISDP8TP1U5OS/ke17ZwdGBToddI8pDm48kHa5HH41tqM2_ok8qxQoD7sUqsxRUqqbr1mOJYKfIPR7LoDQ9mXPOjoJoqy81S2I8N_N4V1vUb5AoIIIbLZhVYxCRW4BPu10St3TBAUQYVKcozICIz8_neWFPRbxXThi3cYN0VEmChQbELpN8XWDm3zYfgKoEPNs3BrZ2_Y8YB0b/banner-logo-marvel-2.jpg"
      >

      <template v-slot:extension>
        <v-tabs align-with-title>
          <v-tab><v-icon>mdi-magnify</v-icon></v-tab>
        </v-tabs>
      </template>

      </v-app-bar>

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
export default {
  name: 'DefaultLayout',
  data() {
    return {
      title: 'MARVEL',
    }
  },
}
</script>

<style>

</style>

