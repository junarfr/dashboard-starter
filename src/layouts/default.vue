<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" fixed app>
      <h3 class="py-3 text-center" v-text="title" />
      <v-list>
        <v-list-item
          :ripple="false"
          active-class="warning--text secondary"
          class="mx-3 my-1"
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-content class="accent">
      <v-container>
        <v-flex row>
          <v-btn
            fab
            small
            text
            outlined
            :ripple="false"
            @click.stop="drawer = !drawer"
          >
            <v-icon color="secondary">
              {{ drawer ? mdiMenuOpen : mdiMenu }}
            </v-icon>
          </v-btn>
          <v-breadcrumbs :items="item"></v-breadcrumbs>
        </v-flex>
        <nuxt class="mt-5" />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import {
  mdiViewDashboardOutline,
  mdiBookOutline,
  mdiMenu,
  mdiMenuOpen,
  mdiPrinterCheck,
  mdiTableChair
} from "@mdi/js"

export default {
  data() {
    return {
      drawer: window.innerWidth > 700 ? true : false,
      fixed: false,
      mdiMenu,
      mdiMenuOpen,
      items: [
        {
          icon: mdiViewDashboardOutline,
          title: "Beranda",
          to: "/"
        },
        {
          icon: mdiBookOutline,
          title: "Order",
          to: "/order"
        },
        {
          icon: mdiPrinterCheck,
          title: "Revenue",
          to: "/revenue"
        },
        {
          icon: mdiTableChair,
          title: "Assets",
          to: "/assets"
        }
      ],
      item: [
        {
          text: "Dashboard",
          disabled: false,
          href: "breadcrumbs_dashboard"
        },
        {
          text: "Link 1",
          disabled: false,
          href: "breadcrumbs_link_1"
        },
        {
          text: "Link 2",
          disabled: true,
          href: "breadcrumbs_link_2"
        }
      ],
      title: "Vuetify.js"
    }
  }
}
</script>

<style>
#app {
  /* font-family: "Work Sans", sans-serif !important; */
  font-family: "90", sans-serif !important;
}
.page {
  background: white !important;
}
</style>
