<script setup lang="ts">
import { ref } from 'vue';
import '../../styles/header.css';

defineProps<{ text: string }>();
</script>

<template>
  <div class="header right-align">
    <div>{{ text }}</div>
    <div>👤</div>
  </div>
</template>
