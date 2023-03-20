<template>
    <div class="container">
    <h1 class="text-dark text-center">surat masuk</h1>
    <NuxtLink to="/tambah" class="btn btn-primary mb-3">Tambah</NuxtLink>
    <button @click="logout()" class="btn btn-danger">keluar</button>
        <h3>test</h3>
    <table border ="1" width="50%" class="table bg-light w-full">
    <thead>
    <tr>
    <th>no</th>
    <th>tanggal</th>
    <th>nomorsurat</th>
    <th>dari</th>
    <th>tujuan</th>
    <th>perihal</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="(visitor,i) in datas" :key="visitor.id">
        <td>{{ i+1 }}</td>
    
    <td>{{ visitor.created_at }}</td>
    <td>{{ visitor.nomor_surat }}</td>
    <td>{{ visitor.dari }}</td>
    <td>{{ visitor.tujuan }}</td>
    <td>{{ visitor.perihal }}</td>
    </tr>
    </tbody>
    </table>
    </div>
</template>

<script setup >
const supa = useSupabaseAuthClient()
const supabase = useSupabaseClient()
const datas = ref([])

async function getData() {
 const { data, error } = await supa
 .from("surat")
 .select()
 datas.value = data
 console.log(datas.value)
}

onMounted(() => {
 getData()
})
</script>
<style>
.p{
    margin-right: 10px;
}
</style>