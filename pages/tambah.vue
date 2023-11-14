<template>
<div class="mb-3">
    <br />
    <h2>Isi Buku Tamu</h2>
    <br />
    <form @submit.prevent="SimpanKunjungan">
    <input v-model="form.nama" type="text" placeholder="Nama ..." required />
    <br />
    <select v-model="form.anggota">
        <option value="">Pilih Anggota</option>

        <option v-for="a in anggota" :key="a.id" :value="a.id">
        {{ a.nama }}
        </option>
    </select>
    <br />
    
    <textarea
        v-model="form.keperluan"
        cols="30"
        rows="10"
        placeholder="Keperluan..."
    ></textarea>
    <br />
    <button type="“submit”" class="btn btn-primary">Kirim</button>
    <NuxtLink to="/" class="btn btn-outline-secondary">Kembali</NuxtLink>
    </form>
</div>
</template>
    
    <script setup>
const supabase = useSupabaseClient();
const anggota = ref([]);
const form = reactive({
nama: "",
anggota: "",
keperluan: "",
});

async function getAnggota() {
const { data, error } = await supabase.from("anggota").select();
if (data) anggota.value = data;
}
async function SimpanKunjungan() {
  //   console.log(form);
const { error } = await supabase.from("pengunjung").insert(form);
}
onMounted(() => getAnggota());
</script>
    
