<template>
  <div class="prose mb-12">
    <ul class="list-none">
      <li>
        <NuxtLink :to="firstLesson.path" class="underline font-medium">Go to First Lesson</NuxtLink>
      </li>
      <li>
        <NuxtLink class="underline font-medium" to="/login">Login</NuxtLink>
      </li>
    </ul>
  </div>

</template>
<script lang="ts" setup>
const firstLesson = useFirstLesson();
</script>
