<template>
<div v-if="user" class="rounded p-3 flex items-center space-x-3 bg-white ">
  <img :src="profile" :alt="name" class="rounded-full w-12 h12 border-2 bg-blue-400">
  <div class="text-right">
    <div class="font-medium">{{name}}</div>
    <button class="text-sm underline text-slate-500" @click="logout">Logout</button>
  </div>
</div>
</template>
<script setup lang="ts">
const user = useSupabaseUser();
const {auth} = useSupabaseClient();

const logout = async () => {
  const {error} = await auth.signOut();
  if(error){
    console.log(error);
    return;
  }

  try {
    await $fetch('api/_supabase/session', {
      method: 'POST',
      body: {event: 'SIGNED_OUT', session: null}
    });
    user.value = null;
  } catch (e) {
    console.error(e);
  }

  await navigateTo('/')
}

const name = computed(
    () =>  user.value?.user_metadata.full_name
);

const profile = computed(
    () => user.value?.user_metadata.avatar_urls
);
</script>
