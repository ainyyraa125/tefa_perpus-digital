<template>
    <div>
      <h1>tunggu sebentar.....</h1>
    </div>
  </template>

  <script setup>
  useHead({ title: "PRESENSI", meta: [{ name: "description", content: "HALAMAN LOGOUT PRESENSI SISWA SMKN 4 TASIKMALAYA" }] });
  const supabase = useSupabaseClient();
  
  async function logout() {
    const { error } = await supabase.auth.signOut();
    if (!error) navigateTo("/login");
  }
  
  onMounted(() => {
    logout();
  });
  </script>