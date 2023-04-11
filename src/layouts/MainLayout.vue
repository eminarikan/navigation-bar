<template>
  <q-layout view="hHh lpR fFf">
    <q-header class="bg-primary text-white" height-hint="98">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" />
          </q-avatar>
          Title
        </q-toolbar-title>
        <q-toggle v-model="drawer" color="green" label="Change Nav" />
      </q-toolbar>
      <q-tabs
        align="center"
        v-if="!drawer"
        active-color="negative"
        dense
        no-caps
        outside-arrows
        mobile-arrows
      >
        <q-route-tab
          v-for="link in essentialLinks"
          :key="link.title"
          :to="link.link"
          :label="link.title"
          :icon="link.icon"
        ></q-route-tab>
      </q-tabs>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered v-if="drawer">
      <q-list>
        <q-tabs
          vertical
          inline-label
          no-caps
          outside-arrows
          mobile-arrows
          dense
          active-color="negative"
        >
          <q-route-tab
            v-for="link in essentialLinks"
            :key="link.title"
            :to="link.link"
            :label="link.title"
            :icon="link.icon"
            class="column content-start"
          ></q-route-tab>
        </q-tabs>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from "vue";

const drawer = ref(false);

const essentialLinks = [
  {
    title: "Docs",
    caption: "quasar.dev",
    icon: "school",
    link: "https://quasar.dev",
  },
  {
    title: "Github",
    caption: "github.com/quasarframework",
    icon: "code",
    link: "https://github.com/quasarframework",
  },
  {
    title: "Discord Chat Channel",
    caption: "chat.quasar.dev",
    icon: "chat",
    link: "https://chat.quasar.dev",
  },
  {
    title: "Forum",
    caption: "forum.quasar.dev",
    icon: "record_voice_over",
    link: "https://forum.quasar.dev",
  },
  {
    title: "Twitter",
    caption: "@quasarframework",
    icon: "rss_feed",
    link: "https://twitter.quasar.dev",
  },
  {
    title: "Facebook",
    caption: "@QuasarFramework",
    icon: "public",
    link: "https://facebook.quasar.dev",
  },
  {
    title: "Quasar Awesome",
    caption: "Community Quasar projects",
    icon: "favorite",
    link: "https://awesome.quasar.dev",
  },
];

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
function toggleNav() {
  drawer.value = !drawer.value;
}
</script>
<style>
.b {
  border: 1px solid black;
}
</style>
