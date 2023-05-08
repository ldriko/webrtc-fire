<script lang="ts" setup>
import { ref, watch } from 'vue';

const emit = defineEmits<{
  (e: 'update:modelValue', value: string);
}>();

const props = withDefaults(
  defineProps<{
    modelValue?: string | number;
    type?: 'text' | 'number' | 'multiline';
    placeholder?: string;
  }>(),
  {
    type: 'text'
  }
);

const model = ref(props.modelValue as string);

watch(model, (v) => emit('update:modelValue', v));
</script>

<template>
  <input
    v-model="model"
    :type="type"
    :placeholder="placeholder"
    class="px-4 py-2 border rounded-lg focus:outline focus:outline-2"
  />
</template>
