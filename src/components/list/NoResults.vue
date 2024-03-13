<script setup lang="ts">
import { ref } from 'vue';

defineProps<{ msg: String }>();
</script>

<template>
  <div>{{ msg }}</div>
</template>

<style scoped>
div {
  padding: 20px 32px;
  font-weight: 600;
}
</style>
