<script setup lang="ts">
defineProps<{ title: string; content: string; }>()
</script>

<template>
  <div class="anounce">
    <h5>{{title}}</h5>
    <p>
      {{content}}
    </p>
  </div>
  <slot />
</template>