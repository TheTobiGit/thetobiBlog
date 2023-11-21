<template>
  <div class="flex flex-col justify-center items-center h-[80vh] gap-3">
    <h1 class="text-4xl">LOGIN</h1>
    <div class="flex flex-col gap-2">
      <label for="email">email:</label>
      <input
        type="email"
        name="email"
        id="email"
        class="w-30 border border-black"
      />
    </div>
    <div class="flex flex-col gap-2">
      <label for="password">password:</label>
      <input
        type="password"
        name="password"
        id="password"
        class="w-30 border border-black"
      />
    </div>
    <div class="flex gap-2">
      <button>submit</button>
      <p>|</p>
      <NuxtLink to="/signup"><p>sign up</p></NuxtLink>
    </div>
  </div>
</template>

<script setup>
definePageMeta({
  layout: "auth",
});
</script>
