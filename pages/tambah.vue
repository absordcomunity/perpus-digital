<template>
    <div>
        <h1>Isi Buku Tamu</h1>
        <form @submit.prevent="simpan()">
            <input v-model="id" placeholder="id"> <br />
            <input v-model="tanggal" placeholder="tanggal"> <br />
            <input v-model="waktu" placeholder="waktu"> <br />
            <input v-model="nama" placeholder="nama"> <br />
            <input v-model="anggota" placeholder="anggota"> <br />
            <input v-model="keperluan" placeholder="keperluan"> <br />
        </form>
    </div>
    </template>
    
    <script setup>
    const supabase = useSupabaseClient()
    const id = ref()
    const tanggal = ref()
    const waktu = ref()
    const nama = ref()
    const anggota = ref()
    const keperluan = ref()
    
    async function simpan() {
        await supabase
        .form("pengunjung")
        .insert({
            id: id.value,
            tanggal: tanggal.value,
            waktu: waktu.value,
            nama: nama.value,
            anggota: anggota.value,
            keperluan: keperluan.value,
        })
        navigateTo("/")
    }
    </script>
    
    <style>
    
    </style>