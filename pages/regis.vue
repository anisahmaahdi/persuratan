<template>
    <div>
        <form @submit.prevent="Signup()">
            <input type="email" v-model="email" /><br/>
            <input type="password" v-model="password" />
            <button type="submit">daftar</button>
        </form>
    </div>
</template>

<script setup>
const supabase = useSupabaseAuthClient();

const email = ref();
const password = ref();

async function Signup() {
  const { user, data, error } = await supabase.auth.signUp({
    email: email.value,
    password: password.value,
  });
  console.log(user);
}
</script>