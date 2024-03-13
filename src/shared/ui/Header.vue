<script setup lang="ts">
import { ref } from 'vue';
import '../../styles/header.css';

defineProps<{ text: string }>();

const emit = defineEmits<{ openSidebar: (isOpen: Boolean) => void }>();

function onOpenSidebar() {
  emit('openSidebar', true);
}

</script>

<template>
  <div class="header right-align">
    <div>☰</div>
    <div class="avatar" @click="onOpenSidebar">{{ text }} 👤</div>
  </div>
  
</template>


<style scoped>

.avatar{
  cursor: pointer;
}
</style>