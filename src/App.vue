<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
import { createRouter, createWebHistory } from 'vue-router';
import HomePage from './components/HomePage.vue';
import LecturerPage from './components/LecturerPage.vue';

const routes = [
  {
    path: '/',
    name: 'HomePage',
    component: HomePage,
  },
  {
    path: '/lecturer',
    name: 'LecturerPage',
    component: LecturerPage,
  },
  // Add more routes here if needed
];

const router = createRouter({
  history: createWebHistory(process.env.BASE_URL),
  routes,
});

export default {
  name: 'App',
  router,
};
</script>

<style>
/* Global styles */
</style>
