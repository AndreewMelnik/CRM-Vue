<template>
  <v-app id="inspire">
    <v-app-bar
        app
        class="app-bar"
        clipped-left
        color="#00E5FF"
        dense
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title class="mr-12 align-center">
        <NuxtLink to="/">
          <span class="title">Vuetify-CRM</span>
        </NuxtLink>
      </v-toolbar-title>
      <v-row
          align="center"
          class="mx-4"
          style="max-width: 650px"
      >
        <v-text-field
            :append-icon-cb="() => {}"
            append-icon="mdi-magnify"
            color="white"
            hide-details
            placeholder="Search..."
            single-line
        ></v-text-field>
      </v-row>
    </v-app-bar>

    <v-navigation-drawer
        v-model="drawer"
        app
    >
      <v-sheet
          class="pa-4 d-flex flex-column align-center"
      >
        <VAvatar
            class="my-4"
            color="primary"
            style="cursor: pointer;"
            variant="tonal"
        >
          <img :src="avatarImg"/>
        </VAvatar>
        <div>john@vuetifyjs.com</div>
      </v-sheet>

      <v-divider></v-divider>

      <v-list>

        <span
            v-for="[text, link] in links"
            :key="link"
            class="link"

        >
          <NuxtLink
              :to="link">
            <v-btn class="nav-btn">{{ text }} </v-btn>
          </NuxtLink>
        </span>
      </v-list>
    </v-navigation-drawer>

    // main page content
    <v-main>
      <v-container
          class="py-8 px-6"
          fluid
      >
        <slot/>
      </v-container>
    </v-main>

  </v-app>
</template>

<script>

export default {
  name: "default.vue",
  data: () => ({
    cards: ['Today', 'Yesterday'],
    drawer: null,
    links: [
      ['Contacts', 'contacts'],
      ['Conversations', 'conversations'],
      ['Marketing', 'marketing'],
      ['Sales', 'sales'],
      ['Service', 'service'],
    ],
  }),
}
</script>
<style scoped>
a {
  text-decoration: none !important;
  color: black !important;
}

.nav-btn {
  min-height: 48px;
  width: -webkit-fill-available;
  border: none !important;
  box-shadow: none !important;
  /*align-items: center;*/
  /*display: grid;*/
  /*flex: none;*/
  /*grid-template-areas: "prepend content append";*/
  /*grid-template-columns: max-content auto max-content;*/
  /*outline: none;*/
  /*max-width: 100%;*/
  /*padding: 4px 16px;*/
  /*position: relative;*/
}

.app-bar {
  box-shadow: none !important;
  z-index: 1;
}
</style>