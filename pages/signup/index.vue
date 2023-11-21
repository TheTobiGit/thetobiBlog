<script setup>
import { ref } from "vue";

const supabase = useSupabaseClient();

definePageMeta({
  layout: "auth",
});

let email;
let password;
let firstName, lastName;
const errormsg = ref(null);

async function signup() {
  const { data, error } = await supabase.auth.signUp({
    email: email,
    password: password,
    options: {
      data: {
        firstName: firstName,
        lastName: lastName,
      },
    },
  });

  if (error) {
    errormsg.value = error.message;
    return;
  }

  navigateTo("/");
}
</script>

<template>
  <div class="flex flex-col justify-center items-center h-[80vh] gap-3">
    <h1 class="text-4xl">SIGNUP</h1>
    <form @submit.prevent="signup">
      <div class="flex flex-col gap-2">
        <label for="firstName">First Name:</label>
        <input
          type="text"
          name="firstName"
          id="firstName"
          class="w-30 border border-black"
          v-model="firstName"
        />
      </div>
      <div class="flex flex-col gap-2">
        <label for="lastName">Last Name:</label>
        <input
          type="text"
          name="lastName"
          id="lastName"
          class="w-30 border border-black"
          v-model="lastName"
        />
      </div>
      <div class="flex flex-col gap-2">
        <label for="email">email:</label>
        <input
          type="email"
          name="email"
          id="email"
          class="w-30 border border-black"
          v-model="email"
        />
      </div>
      <div class="flex flex-col gap-2">
        <label for="password">password:</label>
        <input
          type="password"
          name="password"
          id="password"
          class="w-30 border border-black"
          v-model="password"
        />
      </div>
      <div class="flex justify-center gap-2">
        <button type="submit">submit</button>
        <p>|</p>
        <NuxtLink to="/login"><p>login</p></NuxtLink>
      </div>
    </form>
    <p class="text-red-500">{{ errormsg }}</p>
  </div>
</template>
