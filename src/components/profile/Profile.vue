<script setup lang="ts">
import { ref } from 'vue';
import '../../styles/profile.css';

defineProps<{ isSidebarOpen: Boolean }>();

const emit = defineEmits<{ openSidebar: (isOpen: Boolean) => void }>();


function onCloseSideBar() {
  emit('openSidebar', false);
}

</script>

<template>
  <div class="sidebar" :class="{ 'show': isSidebarOpen }">
    <!-- Sidebar content goes here -->
    <div class="user-profile-close" @click="onCloseSideBar" >❌</div>
    <div class="user-profile">
            <img src="https://via.placeholder.com/150" alt="User Avatar">
            <div class="user-details">
                <h3>Adelina</h3>
                <p>Adelina Fake Profile</p>
            </div>
    </div>
       
    
    <!-- Sidebar content goes here -->
    <ul>
      <li>Menu Item 1</li>
      <li>Menu Item 2</li>
      <li>Menu Item 3</li>
    </ul>

  </div>
</template>
