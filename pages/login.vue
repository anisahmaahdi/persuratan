<template>
    <div>
        <form @submit.prevent="masuk">
            <input type="email" v-model="email" class="form-control" /><br />
            <input type="password" v-model="password" />
            <button type="submit" >login</button>
        </form>
    </div>
</template>

<script setup>

const supabase = useSupabaseAuthClient();
const user = useSupabaseUser()
console.log(user)
const email = ref();
const password = ref();
async function masuk(){
    const { user,data,error } = await supabase.auth.signInWithPassword({
        email: email.value,
        password: password.value,
    });
console.log(user);
navigateTo("/");
}
</script>