<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <div class="my-3">
          <form @submit.prevent="getpengunjung">
            <input v-model="keyword" type="search" class="form-control rounded-5" placeholder="Filter" />
          </form>
        </div>
        <div class="my-3 text-muted">menampilkan {{ visitors.length }} dari {{ visitors.length }}</div>
        <table class="table">
          <thead>
            <tr class="text-center">
              <th>#</th>
              <th>NAMA</th>
              <th>KEANGGOTAAN</th>
              <th>TINGKAT</th>
              <th>JURUSAN</th>
              <th>KELAS</th>
              <th>KEPERLUAN</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(visitor, i) in visitors" :key="i">
              <td>{{ i + 1 }}.</td>
              <td>{{ visitor.nama }}</td>
              <td>{{ visitor.keanggotaan.nama }}</td>
              <td>{{ visitor.tingkat }}</td>
              <td>{{ visitor.jurusan }}</td>
              <td>{{ visitor.kelas }}</td>
              <td>{{ visitor.keperluan.nama }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <NuxtLink to="/pengunjung/tambah"><button type="submit" class="btn btn-lg btn-dark rounded-5 px-5 bg-secondary text-white" style="float: right; margin-bottom: 15px">KEMBALI</button></NuxtLink>
  </div>
</template>

<script setup>
useHead({ title: "pengunjung perpus" });
const supabase = useSupabaseClient();

const visitors = ref([]);
const keyword = ref("");
const jumlah = ref(0);

const getpengunjung = async () => {
  const { data, error } = await supabase.from("pengunjung").select(`*, keanggotaan(*), keperluan(*)`).ilike("nama", `%${keyword.value}%`).order(`id`, { ascending: false });
  if (data) visitors.value = data;
};

const totalpengunjung = async () => {
  const { data, count } = await supabase.from("pengunjung").select("*", { count: "exact" });
  if (data) jumlah.value = count;
};

onMounted(() => {
  getpengunjung();
  totalpengunjung();
});
</script>
