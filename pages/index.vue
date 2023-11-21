<script setup>
const supabase = useSupabaseClient();

const {
  data: { user },
} = await supabase.auth.getUser();

console.log(user.email);
</script>

<template>
  <div class="flex justify-center items-center">
    <p>This is the home page</p>
  </div>
</template>
