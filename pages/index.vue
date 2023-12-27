<template>
  <div class="prose mb-12">
    <NuxtLink :to="firstLesson.path" class="underline font-medium">Go to First Lesson</NuxtLink>
  </div>

</template>
<script lang="ts" setup>
const firstLesson = useFirstLesson();
</script>
