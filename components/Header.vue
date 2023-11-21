<script setup>
const supabase = useSupabaseClient();

async function signout() {
  const { error } = await supabase.auth.signOut();

  navigateTo("/login");
}

const {
  data: { user },
} = await supabase.auth.getUser();

const userMail = user.email;
</script>

<template>
  <div class="flex justify-center items-center h-[5vh] gap-5">
    <ul class="flex gap-3">
      <NuxtLink to="/"><li>Home</li></NuxtLink>
      <NuxtLink to="/addpost"><li>Add Post</li></NuxtLink>
      <NuxtLink to="/viewposts"><li>View Posts</li></NuxtLink>
    </ul>
    <button @click="signout">SignOut</button>
    <p>{{ userMail }}</p>
  </div>
</template>
