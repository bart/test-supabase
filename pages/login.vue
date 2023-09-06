<script setup lang="ts">
const supabase = useSupabaseClient();

const email = ref("");
const password = ref("");

const login = async () => {
  const { error } = await supabase.auth.signInWithPassword({
    email: email.value,
    password: password.value,
  });

  if (!error) {
    await navigateTo("/");
  }
};
</script>

<template>
  <div>
    <input type="text" v-model="email" />
    <input type="password" v-model="password" />
    <button @click="login">Login</button>
  </div>
</template>
