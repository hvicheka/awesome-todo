<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"

        />

        <q-toolbar-title class="absolute-center">
          Awesome Todo
        </q-toolbar-title>

      </q-toolbar>
    </q-header>
    <q-footer reveal elevated>
      <q-tabs>
        <q-route-tab v-for="link in sideBarLinks" :to="link.link" :icon="link.icon" :label="link.title" exact/>
      </q-tabs>
    </q-footer>
    <q-drawer
      v-model="leftDrawerOpen"
      :breakpoint="767"
      :width="250"
      show-if-above
      bordered
      content-class="bg-primary"
    >
      <q-list>
        <SideBar
          v-for="link in sideBarLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view/>
    </q-page-container>
  </q-layout>
</template>

<script>
import SideBar from 'components/Sidebar.vue'

const linksData = [
  {
    title: 'Todo',
    icon: 'list',
    link: '/'
  },
  {
    title: 'Setting',
    icon: 'settings',
    link: '/settings'
  }
];

export default {
  name: 'MainLayout',
  components: {
    SideBar
  },
  data() {
    return {
      leftDrawerOpen: false,
      sideBarLinks: linksData
    }
  }
}
</script>

<style lang="css">

@media only screen and (min-width: 767px) {
  .q-footer {
    display: none;
  }
}
</style>
