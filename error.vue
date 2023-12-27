<template>
  <NuxtLayout>
    <div v-if="error.statusCode === 404" class="prose">
      <h1>404</h1>
      <p>I guess that page doesn't exist.</p>
    </div>
    <div v-else class="prose">
      <h1>Dang</h1>
      <p>It looks like something broke</p>
      <p>Sorry about that.</p>
    </div>
    <p><strong>{{error.message}}</strong></p>
    <button class="rounded text-white font-bold py-2 px-4 my-8 cursor-pointer bg-gray-500" @click="handleError()">Go back to Course</button>
  </NuxtLayout>
</template>
<script setup>
const error = useError();

const handleError = () => {
  clearError({redirect:'/course'})
}
</script>