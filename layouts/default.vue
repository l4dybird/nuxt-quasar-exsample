<script setup lang="ts">
import { ref } from '@nuxtjs/composition-api'
const selectedTab = ref('');

const onTabSelected = (tab: string) => {
    selectedTab.value = tab;
};

const onTabReset = () => {
    selectedTab.value = '';
};

const onTabClick = (tab: string) => {
    if(selectedTab.value) {
        onTabReset();
    } else {
        onTabSelected(tab);
    }
};

const isShowTab = (tab: string): boolean => {
    return selectedTab.value === tab;
};

const tabNames = {
    mails: 'mails',
    alarms: 'alarms',
    movies: 'movies'
}
</script>

<template>
  <div>
      <q-tabs
        v-model="selectedTab"
        no-caps
        outside-arrows
        mobile-arrows
        class="bg-orange text-white shadow-2"
      >
        <q-tab name="mails" label="Mails" @click="onTabClick(tabNames.mails)" @mouseover="onTabSelected(tabNames.mails)"></q-tab>
        <q-tab name="alarms" label="Alarms" @click="onTabClick(tabNames.alarms)" @mouseover="onTabSelected(tabNames.alarms)"></q-tab>
        <q-tab name="movies" label="Movies" @click="onTabClick(tabNames.movies)" @mouseover="onTabSelected(tabNames.movies)"></q-tab>
      </q-tabs>
      <q-toolbar v-show="isShowTab(tabNames.mails)" class="bg-primary text-white" @mouseleave="onTabReset()">
        <q-btn flat dense label="mails" @click="onTabReset"></q-btn>
      </q-toolbar>
      <q-toolbar v-show="selectedTab === 'alarms'" class="bg-primary text-white" @mouseleave="onTabReset()">
        <q-btn flat dense label="alarms" @click="onTabReset"></q-btn>
      </q-toolbar>
      <q-toolbar v-show="selectedTab === 'movies'" class="bg-primary text-white" @mouseleave="onTabReset()">
        <q-btn flat dense label="movies" @click="onTabReset"></q-btn>
      </q-toolbar>
      <Nuxt />
  </div>
</template>