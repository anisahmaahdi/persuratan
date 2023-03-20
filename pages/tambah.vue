<template>
    <div>
    <h1>surat masuk</h1>
    <form @submit.prevent="simpan">
    <select v-model="jenis">
        <option value="masuk">Surat Masuk</option>
        <option value="keluar">Surat Keluar</option>
    </select>

    <input v-model="nomorsurat" placeholder="nomor surat"> <br>
    <input v-model="dari" placeholder="dari"> <br> 
    <input v-model="tujuan" placeholder="tujuan"> <br>
    <input v-model="perihal" placeholder="perihal"> <br>
    
<button type="submit">kirim</button>
<NuxtLink to="/">keluar</NuxtLink>
    </form>
    </div>
</template>

<script setup>
definePageMeta({
  middleware: 'auth'
})
const supabase = useSupabaseClient()
const jenis = ref()

const nomorsurat = ref()
const dari = ref()
const tujuan = ref()
const perihal = ref()

async function simpan() {
await supabase 
.from("sm") 
.insert({
    nomorsurat: nomorsurat.value,
    dari: dari.value,
    tujuan: tujuan.value,
    perihal: perihal.value,
    jenis: jenis.value,   
})  
navigateTo("/");
}
</script>