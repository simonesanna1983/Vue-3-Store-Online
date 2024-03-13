<script setup lang="ts">
import { ref } from 'vue';
import '../../styles/footer.css';

defineProps<{ text: string }>();
</script>

<template>
  <div class="footer">{{ text }}</div>
</template>
