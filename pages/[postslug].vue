<script setup>
const route = useRoute();
const slug = route.params.postslug;
</script>

<template>
  <div class="text-2xl mt-4">
    {{ slug }}
  </div>
</template>
