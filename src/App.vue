<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
    >
    <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            Vuetify-Todo
          </v-list-item-title>
          <v-list-item-subtitle>
            Best To-do list ever!
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to = "item.to"
          link
        >
          <v-list-item-icon>
            <v-icon 
            large
            color="pink darken-2">{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar 
      app
      color="primary"
      dark
      src="https://picsum.photos/1920/1080?random"
      prominent
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>Vuetify Todo</v-app-bar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>

    <v-footer padless>
    <v-card
      class="flex"
      flat
      tile
    >
      <v-card-title class="teal">
        <span class="subheading">Get connected with me on social networks!</span>

        <v-spacer></v-spacer>

        <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-4"
          dark
          icon
        >
          <v-icon size="24px" >
            {{ icon }}
          </v-icon>
        </v-btn>
      </v-card-title>

      <v-card-text class="py-2 dark--text text-center">
        {{ new Date().getFullYear() }} — <strong>@priuet</strong>
      </v-card-text>
    </v-card>
  </v-footer>

  </v-app>
</template>

<script>
  export default {
    data: () => ({ 
        drawer: null,
        items: [
          { title: 'Todo', icon: 'mdi-format-list-checks', to:'/' },
          { title: 'About', icon: 'mdi-help-box', to: '/about' },
        ],
        icons: [
        'mdi-github',
        'mdi-telegram',
        'mdi-instagram',
      ]
      }),
  }
</script>

