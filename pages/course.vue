<template>
  <div>
    <div class="prose mb-12">
      <h1>
        <span class="font-medium">
          Course:
          <span class="font-bold">Mastering Nuxt 3</span>
        </span>
      </h1>
    </div>

    <div class="flex flex-row justify-center flex-grow">
      <div
          class="prose mr-4 p-8 bg-white rounded-md min-w-[20ch] flex flex-col max-w-[30ch]"
      >
        <h3>Chapters</h3>
        <!-- All the lessons for the course listed here -->
        <div
            v-for="chapter in chapters"
            :key="chapter.slug"
            class="flex flex-col space-y-1 mb-4"
        >
          <h4>{{ chapter.title }}</h4>
          <NuxtLink
              v-for="(lesson, index) in chapter.lessons"
              :key="lesson.slug"
              :class="{
                'text-blue-500': lesson.path === $route.fullPath,
                'text-gray-600': lesson.path !== $route.fullPath}"
              :to="lesson.path"
              class="flex flex-row space-x-1 no-underline prose-sm font-normal py-1 px-4 -mx-4"
          >
          <span class="text-gray-500"
          >{{ index + 1 }}.</span
          >
            <span>{{ lesson.title }}</span>
          </NuxtLink>
        </div>
      </div>

      <div class="prose p-12 bg-white rounded-md w-[65ch]">
        <NuxtErrorBoundary>
          <NuxtPage/>
          <template #error="{ error }">
            <p>Oh no! Something went wrong with the lesson!
              <code>{{ error }}</code>
            </p>
            <p>
              <button class="rounded text-white font-bold py-2 px-4 cursor-pointer bg-gray-500"
                      @click="resetError(error)">Try Again
              </button>
            </p>
          </template>
        </NuxtErrorBoundary>
      </div>
    </div>
  </div>
</template>

<script setup>
const {chapters} = useCourse();
const resetError = async (error) => {
  await navigateTo('/course/chapter/1-chapter-1/lesson/1-introduction-to-typescript-with-vue-js-3');
  error.value = null;
}
</script>
