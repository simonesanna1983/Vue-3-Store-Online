<script setup lang="ts">
import { ref, defineEmits } from 'vue';

const text = ref<String>([]);

const emit = defineEmits<{ searchCallBack: (data: string) => void }>();

function test(event) {
  console.log('event', event);
  console.log('$event.target.value', event.target.value);

  emit('searchCallBack', text.value);
}
</script>

<template>
  <div class="input-group">
    <input
      @keyup="test"
      v-model="text"
      placeholder="search for title"
      class="form-control search-menu"
    >
    <i class="fa fa-search" aria-hidden="true"></i>
  </input>



  </div>
</template>

<style scoped>
.input-group {
  width: 300px;
}
i {
    margin-left: -30px !important;
    z-index: 999;
    margin-top: 10px;
}
</style>
