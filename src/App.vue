<script lang="ts" setup>
import { ref } from 'vue';
import BaseButton from './components/BaseButton.vue';
import BaseTextField from './components/BaseTextField.vue';

const state = ref<null | 'start' | 'join'>(null);
</script>

<template>
  <div class="max-w-screen-lg m-auto p-8 text-sm">
    <div class="text-xl font-black mb-2">WebRTC Podcast</div>
    <div v-if="!state" class="flex gap-2">
      <BaseButton @click="state = 'start'">Start Podcast</BaseButton>
      <BaseButton color="secondary" @click="state = 'join'"
        >Join Podcast</BaseButton
      >
    </div>
    <div v-if="state === 'start'" class="flex gap-2">
      <BaseTextField placeholder="Enter title" />
      <BaseButton @click="state = null">Start</BaseButton>
    </div>
    <div v-if="state === 'join'" class="flex gap-2">
      <BaseTextField placeholder="Enter code" />
      <BaseButton @click="state = null">Join</BaseButton>
    </div>
  </div>
</template>
