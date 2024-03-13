<script setup lang="ts">
import { ref } from 'vue';

defineProps<{ isCompleted: Boolean }>();
</script>

<template>
  <span v-if="isCompleted">✔️</span>
  <span v-else>❌</span>
</template>

<style scoped>
span {
  margin-left: 25px;
}
</style>
