<script setup lang="ts">
import { ref } from 'vue';
import '../../styles/modal.css';

defineProps<{ todo: Todo; isModalOpen: Boolean }>();

const emit = defineEmits<{ closeModal: () => void }>();

function onCloseModal() {
  emit('closeModal');
}
</script>

<template>
  <!-- Modal -->

  <div class="modal-wrapper-detail" v-if="isModalOpen">
    <div class="modal-detail">
      <div class="header-detail">
        <h2>Todo #: {{ todo.id }}</h2>
        <span class="close-detail" @click="onCloseModal">✖️</span>
      </div>

      <div class="modal-body-detail">
        <br /><br />
        {{ todo.title }}
        <br /><br />
        Sed ut perspiciatis unde omnis iste natus error sit voluptatem
        accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab
        illo inventore veritatis et quasi architecto beatae vitae dicta sunt
        explicabo.
      </div>
    </div>
  </div>
</template>
