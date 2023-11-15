<template>
  <br />
  <h2>Riwayat Kunjungan</h2>
  <NuxtLink to="/tambah" class="btn btn-outline-secondary"
    >Isi Buku Tamu</NuxtLink
  >
  <div>
    <br />
    <table class="table table-striped">
      <thead class="table-dark">
        <tr>
          <th>#</th>
          <th>TANGGAL dan WAKTU</th>
          <th>NAMA</th>
          <th>ANGGOTA</th>
          <th>KELAS</th>
          <th>KEPERLUAN</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="pengunjung in visitors" :key="pengunjung.id">
          <td>{{ pengunjung.id }}</td>
          <td>{{ pengunjung.tanggal }} {{ pengunjung.waktu }}</td>
          <td>{{ pengunjung.nama }}</td>
          <td>{{ pengunjung.anggota.nama }}</td>
          <td>
            <span v-if="pengunjung.kelas">{{ pengunjung.kelas }}</span>
            <span v-else>-</span>
          </td>
          <td>{{ pengunjung.keperluan }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
const client = useSupabaseClient();
const visitors = ref([]);

async function getData() {
  const { data, error } = await client.from("pengunjung").select(`id, tanggal, waktu, nama, anggota(nama), kelas, keperluan`);
  if (data) visitors.value = data;
}

onMounted(() => getData());
</script>