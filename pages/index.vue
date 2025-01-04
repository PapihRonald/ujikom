<template>
  <img src="/assets/img/guru1.png" width="100%" />
  <div class="container-fluid">
    <div class="row">
      <div class="card sambutan d-flex bg-secondary">
        <div class="row d-flex">
          <h1 class="text-center text-white pt-3">Selamat Datang</h1>
          <div class="col-lg-3 py-2">
            <img src="/assets/img/kurniawan.png" alt="" />
          </div>
          <div class="col-lg-9 px-4 pt-5 text-white">
            <h6 class="mt-5">Assalamu'alaikum Warahmatullahi Wabarakatuh</h6>
            <p class="sambutan">
              Selamat datang di SMK Negeri 4 TASIKMALAYA. Segala puji dan syukur
              kita panjatkan kehadirat Allah SWT, semoga kita semua ada dalam
              lindungan-Nya. Dan atas perkenan-Nya pula kami dapat menghadirkan
              website SMK Negeri 4 TASIKMALAYA ini. Kami berharap dengan adanya
              website di SMK Negeri 4 TASIKMALAYA ini para pengunjung dapat
              mengenal lebih jauh tentang sekolah kami sehingga dapat mempererat
              tali silaturahmi antara sekolah dengan masyarakat demi kemajuan
              kita bersama. Tiada gading yang tak retak, website kami ini masih
              dalam proses pengembangan, masih banyak kekurangan yang harus kami
              perbaiki. Kritik dan sarannya yang membangun sangat kami harapkan
              untuk pengembangan ke depan. Akhirnya, saya mengucapkan
              terimakasih yang sebesar-besarnya kepada semua pihak yang tidak
              dapat disebutkan satu segala bantuan dan persatu atas fasilitasnya
              yang telah diberikan semoga semua yang kita lakukan bermanfaat
              bagi masyarakat. Wassalamu'alaikum Warahmatullahi Wabarakatuh
            </p>
          </div>
        </div>
      </div>
      <h1 class="text-center py-3">Berita</h1>
      <div
        v-for="(get, i) in berita"
        :key="i"
        class="col-lg-3 d-flex justify-content-center pb-5"
      >
        <div class="card" style="width: 18rem">
          <img :src="get.poto" class="card-img-top" alt="..." />
          <div class="card-body">
            <p class="card-text">
              {{ get.nama }}
            </p>
          </div>
        </div>
      </div>

      <div class="container bg-secondary text-white mb-5">
        <h1 class="text-center py-3">Data Statistik</h1>
        <div class="row">
          <div class="col">
            <h5 class="text-center">Jumlah Siswa</h5>
            <h2 class="text-center display-3">1500</h2>
          </div>
          <div class="col">
            <h5 class="text-center">Guru</h5>
            <h2 class="text-center display-3">85</h2>
          </div>
          <div class="col">
            <h5 class="text-center">Rombel</h5>
            <h2 class="text-center display-3">45</h2>
          </div>
          <div class="col">
            <h5 class="text-center">Tenaga Administrasi</h5>
            <h2 class="text-center display-3">10</h2>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.sambutan {
  text-align: justify;
}
</style>

<script setup>
const supabase = useSupabaseClient();

const berita = ref([]);

const getData = async () => {
  const { data } = await supabase.from("berita").select(`*`);
  if (data) berita.value = data;
};

onMounted(() => {
  getData();
});
</script>
