<template>
    <div>
        <h1>pengunjung</h1>
        <NuxtLink to="/tambah">ISI PENGUNJUNG</NuxtLink>
        <table border="1" width="50%"></table>
            <tbody>
                <tr v-for="visitor in visitors" :key="visitor.id">
                    <td>{{ visitor.id }}</td>
                    <td>{{ visitor.tanggal }}</td>
                    <td>{{ visitor.waktu }}</td>
                    <td>{{ visitor.nama }}</td>
                    <td>{{ visitor.anggota }}</td>
                    <td>{{ visitor.keperluan }}</td>
                </tr>
            </tbody>
    </div>
</template>

<script setup>
const supabase =useSupabaseClient()
const visitors =ref([])

async function getData() {
    const {data,error} =await supabase
    .from ("pengunjung")
    .select()
    visitors.value = data
}
onMounted( () => {
    getData()
})
</script>