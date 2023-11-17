<template>
  <div>
    <h2>Isi Buku Tamu</h2>
    <br />
    <div v-if="sukses" class="alert alert-success">Berhasil Tersimpan!</div>
    <form @submit.prevent="simpan()">
      <div class="mb-3">
        <input v-model="form.nama" type="text" placeholder="Nama" class="form-control" />
      </div>
      <div class="mb-3">
        <label for="exampleFormControlSelect1">Keanggotaan</label>
        <select v-model="form.anggota"  placeholder="Keanggotaan" class="form-control">
          <option value="1">Siswa</option>
          <option value="2">Guru</option>
          <option value="3">Staf</option>
          <option value="4">umum</option>
        </select>
      </div>
      <div v-if="form.anggota == 1" class="mb-3">
           <label for="exampleFormControlSelect1">Kelas</label>
        <select v-model="form.kelas" class="form-control" placeholder="kelas">
             <option value="X PPLG 1">X PPLG 1</option> 
             <option value="X PPLG 2">X PPLG 2</option> 
             <option value="X PPLG 3">X PPLG 3</option> 
             <option value="X PPLG 4">X PPLG 4</option> 
             <option value="X TJKT 1">X TJKT 1</option> 
             <option value="X TJKT 2">X TJKT 2</option> 
             <option value="X TJKT 3">X TJKT 3</option> 
             <option value="X TJKT 4">X TJKT 4</option> 
             <option value="X TBSM 1">X TBSM 1</option> 
             <option value="X TBSM 2">X TBSM 2</option> 
             <option value="X TBSM 3">X TBSM 3</option> 
             <option value="X TBSM 4">X TBSM 4</option> 
             <option value="X DKV 1">X DKV 1</option> 
             <option value="X DKV 2">X DKV 2</option> 
             <option value="X TOI 1">X DKV 1</option> 
             <option value="XI PPLG 1">XI PPLG 1</option> 
             <option value="XI PPLG 2">XI IPPLG 2</option> 
             <option value="XI PPLG 3">XI PPLG 3</option> 
             <option value="XI PPLG 4">XI PPLG 4</option> 
             <option value="XI TJKT 1">XI TJKT 1</option> 
             <option value="XI TJKT 2">XI TJKT 2</option> 
             <option value="XI TJKT 3">XI TJKT 3</option> 
             <option value="XI TJKT 4">XI TJKT 4</option> 
             <option value="XI TBSM 1">XI TBSM 1</option> 
             <option value="XI TBSM 2">XI TBSM 2</option> 
             <option value="XI TBSM 3">XI TBSM 3</option> 
             <option value="XI TBSM 4">XI TBSM 4</option> 
             <option value="XI DKV 1">XI DKV 1</option> 
             <option value="XI DKV 2">XI DKV 2</option> 
             <option value="XI TOI 1">XI TOI 1</option> 
             <option value="XII PPLG 1">XII PPLG 1</option> 
             <option value="XII PPLG 2">XII PPLG 2</option> 
             <option value="XII PPLG 3">XII PPLG 3</option> 
             <option value="XII TJKT 1">XII TJKT 1</option> 
             <option value="XII TJKT 2">XII TJKT 2</option> 
             <option value="XII TJKT 3">XII TJKT 3</option> 
             <option value="XII TBSM 1">XII TBSM 1</option> 
             <option value="XII TBSM 2">XII TBSM 2</option> 
             <option value="XII TBSM 3">XII TBSM 3</option> 
           </select>
      </div>
      <div class="mb-3">
        <textarea v-model="form.keperluan" cols="30" rows="3" placeholder="keperluan" class="form-control"></textarea>
      </div>
      <button type="submit" class="btn btn-primary">Kirim</button>
      <NuxtLink to="/" class="btn btn-outline-secondary">Kembali</NuxtLink>
    </form>
  </div>
</template>
    
<script setup>
const supabase = useSupabaseClient();
const form = reactive({
  nama: "",
  anggota: "",
  kelas: "",
  keperluan: "",
});

const sukses = ref(false);

async function simpan() {
  sukses.value = false;
  const { error } = await supabase.from("pengunjung").insert(form);

  if (!error) {
    sukses.value = true;
    form.nama = ''
    form.anggota = ''
    form.kelas = ''
    form.keperluan = ''
  }
}
</script>
