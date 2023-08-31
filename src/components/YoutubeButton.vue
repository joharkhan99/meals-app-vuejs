<template>
  <a :href="href" target="_blank" class="px-3 py-2 rounded border-2 hover:bg-red-500 hover:text-white border-red-600 bg-red-500">
    <slot>Youtube Button</slot>
  </a>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  href: String
})
</script>