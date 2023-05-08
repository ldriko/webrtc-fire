<script lang="ts" setup>
import { computed } from 'vue';

const props = withDefaults(
  defineProps<{
    color?: 'primary' | 'secondary' | 'error';
  }>(),
  {
    color: 'primary'
  }
);

const colors = computed(() => ({
  'bg-blue-600 outline-blue-300 text-white hover:bg-blue-700':
    props.color === 'primary',
  'bg-white outline-blue-50 text-blue-600 hover:bg-blue-100':
    props.color === 'secondary'
}));
</script>

<template>
  <button
    :class="colors"
    class="px-4 py-2 rounded-lg font-semibold cursor-pointer transition active:outline active:outline-2"
  >
    <slot />
  </button>
</template>
