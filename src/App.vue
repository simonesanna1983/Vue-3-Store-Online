<script setup lang="ts">
import { ref } from 'vue';
import Container from './components/Container.vue';
import Header from './shared/ui/Header.vue';
import Footer from './shared/ui/Footer.vue';

const isSidebarOpen = ref(false);

function handleSidebarCallback(isOpen: boolean) {
   isSidebarOpen.value= isOpen;
}


</script>

<template>
  <Header text="Adelina's Profile" @openSidebar="handleSidebarCallback" />
  <Container :isSidebarOpen="isSidebarOpen" @openSidebar="handleSidebarCallback" />
  <Footer text="This is the Footer" />
</template>
