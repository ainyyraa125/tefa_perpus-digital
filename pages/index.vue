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

    <div class="statistik">
      <h2 class="stat" style="font-family: ; margin-left: 100px">STATISTIK</h2>
    </div>

    <div class="row my-5 justify-content-around">
      <div class="col-lg-6">
        <div class="card bg-pengunjung1 rounded-5">
          <div class="card-body">
            <div class="row">
              <div class="col p-5"><h1 style="font-size: 120px">3</h1></div>
              <div class="col mt-5 p-5"><h2 style="font-family: ; margin-left;-20px">Pengunjung</h2></div>
            </div>
          </div>
        </div>
      </div>

      <div class="col-lg-6">
        <div class="card bg-buku2 rounded-5">
          <div class="card-body">
            <div class="row">
              <div class="col p-5"><h1 style="font-size: 120px">180</h1></div>
              <div class="col mt-5 p-5"><h2 style="font-family: ; margin-left;-20px">Buku</h2></div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <Chart />
  </div>
</template>

<style scoped>
.stat {
  margin-bottom: -100px;
}
.card {
  height: 250px;
  box-shadow: 1px 1px 10px;
}
.card.bg-pengunjung {
  margin-right: 10%;
  margin-left: 10%;
  background-image: url("../assets/img/bg-home-kunjungan.jpeg");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  color: black;
  opacity: 70%;
}

.card.bg-buku {
  margin-right: 10%;
  margin-left: 10%;
  background: url("../assets/img/bg-home-cari-buku.jpg") no-repeat center center;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  color: black;
  opacity: 70%;
}

.card.bg-pengunjung1 {
  margin-right: 10%;
  margin-left: 10%;
  margin-top: 10%;
  background-color: #ece183;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  opacity: 70%;
}
.card.bg-buku2 {
  margin-right: 10%;
  margin-left: 10%;
  margin-top: 10%;
  background-color: #77f6aa;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  opacity: 70%;
}
</style>
