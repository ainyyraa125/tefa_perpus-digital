<template>
  <div class="container-fluid">
    <div class="row my-5">
      <div class="col-lg-6">
        <nuxt-link to="../pengunjung/tambah">
          <div class="card bg-pengunjung rounded-5">
            <div class="card-body">
              <h2>pengunjung</h2>
            </div>
          </div>
        </nuxt-link>
      </div>

      <div class="col-lg-6">
        <nuxt-link to="../buku">
          <div class="card bg-buku rounded-5">
            <div class="card-body">
              <h2>Cari Buku</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>

    <div class="mt-5" style="margin-left: 150px">
      <h2 class="">STATISTIK</h2>
    </div>
    <div class="row my-5 justify-content-around">
      <div class="col-lg-6">
        <div class="card bg-pengunjung1 rounded-5">
          <div class="card-body">
            <nuxt-link to="/pengunjung">
              <div class="row">
                <div class="col p-5">
                  <div class="col p-3" style="font-size: 80px">{{ jumlahp }}</div>
                </div>
                <div class="col mt-5 p-5"><h2 style="font-family: margin-left -20px">Pengunjung</h2></div>
              </div>
            </nuxt-link>
          </div>
        </div>
      </div>

      <div class="col-lg-6">
        <div class="card bg-buku2 rounded-5">
          <div class="card-body">
            <nuxt-link to="./buku">
              <div class="row">
                <div class="col p-5">
                  <h1 style="font-size: 80px; margin-right: 200px">{{ jumlahb }}</h1>
                </div>
                <div class="col mt-5 p-5"><h2 style="font-family: margin-left 20px">Buku</h2></div>
              </div>
            </nuxt-link>
          </div>
        </div>
      </div>
    </div>
    <Chart />
  </div>
</template>

<script setup>
useHead({ title: "perpus digital ainy", meta: [{ name: "description", content: "aplikasi kunjungan dan pencarian buku perpus SMKN 4 TASIKMALAYA" }] });
const supabase = useSupabaseClient();
const jumlahp = ref(0);
const jumlahb = ref(0);

async function ambiljumlahp() {
  const { data, error, count } = await supabase.from("pengunjung").select("*", { count: "exact" });
  if (count) jumlahp.value = count;
}

async function ambiljumlahb() {
  const { data, error, count } = await supabase.from("buku").select("*", { count: "exact" });
  if (count) jumlahb.value = count;
}

onMounted(() => {
  ambiljumlahp();
  ambiljumlahb();
});
</script>

<style scoped>
.card {
  height: 250px;
  box-shadow: 1px 1px 10px;
}
.card.bg-pengunjung {
  margin-right: 13%;
  margin-left: 13%;
  background-image: url("../assets/img/bg-home-kunjungan.webp");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  color: black;
  opacity: 70%;
}

.card.bg-buku {
  margin-right: 13%;
  margin-left: 13%;
  background: url("../assets/img/bg-home-cari-buku.webp") no-repeat center center;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  color: black;
  opacity: 70%;
}

.card.bg-pengunjung1 {
  margin-right: 13%;
  margin-left: 13%;
  margin-top: 2%;
  background-color: #ece183;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  opacity: 70%;
}
.card.bg-buku2 {
  margin-right: 13%;
  margin-left: 13%;
  margin-top: 2%;
  background-color: #77f6aa;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  opacity: 70%;
}
</style>
