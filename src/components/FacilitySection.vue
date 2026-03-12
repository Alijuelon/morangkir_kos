<script setup>
import { ref } from 'vue'

const facilities = ref([
  { 
    // SVG Ikon AC (Warna Hitam akan diterapkan di template)
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v18m0-18l-4 4m4-4l4 4M5 9l14 6m-14 0l4-4m-4 4l4 4M5 15l14-6m-14 0l4 4m-4-4l4-4" />`, 
    title: 'AC Dingin & Bersih', 
    desc: 'Kenyamanan suhu ruangan yang bisa disesuaikan.',
    details: 'Setiap kamar dilengkapi dengan AC Daikin/Panasonic 1/2 PK terbaru yang hemat energi dan diservis secara berkala setiap 3 bulan untuk memastikan udara tetap dingin dan bersih dari debu.'
  },
  { 
    // SVG Ikon WiFi
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8.111 16.404a5.5 5.5 0 017.778 0M12 20h.01m-7.08-7.071c3.904-3.905 10.236-3.905 11.414 0M4.222 9.192a11.002 11.002 0 0115.556 0" />`, 
    title: 'WiFi High-Speed', 
    desc: 'Koneksi stabil untuk WFH atau hiburan tanpa buffering.',
    details: 'Didukung oleh jaringan internet fiber optik berkecepatan hingga 100 Mbps. Setiap lantai memiliki router dedicated sehingga koneksi Anda dijamin stabil untuk meeting Zoom, streaming Netflix 4K, maupun bermain game.'
  },
  { 
    // SVG Ikon Kamar Mandi
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z" />`, 
    title: 'Kamar Mandi Dalam', 
    desc: 'Privasi penuh dengan water heater dan shower premium.',
    details: 'Tidak perlu antre! Kamar mandi dalam dengan dinding keramik elegan, shower bertekanan tinggi, dan water heater canggih. Menggunakan kloset duduk bermerek dan wastafel minimalis.'
  },
  { 
    // SVG Ikon Kasur
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z" />`, 
    title: 'Kasur Springbed', 
    desc: 'Kualitas tidur terbaik dengan set kasur ukuran Queen.',
    details: 'Kami memahami pentingnya istirahat. Oleh karena itu, kami menyediakan Springbed ukuran Queen (160x200cm) dengan teknologi orthopedic, lengkap dengan bantal kepala, guling, dan sprei berbahan katun Jepang yang lembut.'
  },
  { 
    // SVG Ikon Parkir
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7h12m0 0l-4-4m4 4l-4 4m0 6H4m0 0l4 4m-4-4l4-4" />`, 
    title: 'Parkir Luas & Aman', 
    desc: 'Area parkir mobil dan motor dengan pengawasan CCTV 24/7.',
    details: 'Lahan parkir memadai untuk setiap penghuni. Dilengkapi atap kanopi sehingga kendaraan terlindung dari terik matahari dan hujan. Akses keluar masuk menggunakan kartu akses khusus (One Gate System).'
  },
  { 
    // SVG Ikon Kebersihan
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 10h4.764a2 2 0 011.789 2.894l-3.5 7A2 2 0 0115.263 21h-4.017c-.163 0-.326-.02-.485-.06L7 20m7-10V5a2 2 0 00-2-2h-.095c-.5 0-.905.405-.905.905 0 .714-.211 1.412-.608 2.006L7 11v9m7-10h-2M7 20H5a2 2 0 01-2-2v-6a2 2 0 012-2h2.5" />`, 
    title: 'Room Cleaning', 
    desc: 'Layanan kebersihan kamar berkala untuk kenyamanan Anda.',
    details: 'Sibuk bekerja? Biarkan kami yang mengurus kamar Anda. Tersedia layanan pembersihan kamar secara gratis (sweeping, mopping, dan merapikan tempat tidur) yang dapat dijadwalkan seminggu dua kali.'
  }
])

const activeDetail = ref(null)

const openDetail = (item) => {
  activeDetail.value = item
  document.body.style.overflow = 'hidden'
}

const closeDetail = () => {
  activeDetail.value = null
  document.body.style.overflow = 'auto'
}
</script>
<template>
  <section id="fasilitas" class="py-20 relative">
    <div class="text-center mb-16 relative z-10">
      <h2 class="text-4xl md:text-5xl font-bold mb-4 text-slate-900 dark:text-white">Fasilitas <span class="text-gold">Premium</span></h2>
      <p class="text-slate-600 dark:text-slate-400">Pilih fasilitas di bawah ini untuk melihat detail lengkapnya.</p>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 max-w-7xl mx-auto px-4 relative z-10">
      <div v-for="(item, index) in facilities" :key="index" @click="openDetail(item)" class="glass-card p-8 group cursor-pointer">
        <div class="absolute inset-0 -translate-x-full bg-gradient-to-r from-transparent via-white/40 dark:via-white/10 to-transparent group-hover:animate-[shimmer_1.5s_infinite] skew-x-12"></div>
        
        <div class="w-16 h-16 rounded-2xl bg-gradient-to-br from-white to-gray-200 shadow-[0_0_20px_rgba(0,0,0,0.1)] dark:shadow-[0_0_20px_rgba(255,255,255,0.15)] flex items-center justify-center mb-6 transform transition-transform duration-500 group-hover:scale-110 group-hover:rotate-6">
          <svg class="w-8 h-8 text-black drop-shadow-md" fill="none" stroke="currentColor" viewBox="0 0 24 24" v-html="item.icon"></svg>
        </div>
        
        <h3 class="text-2xl font-bold text-slate-900 dark:text-white mb-2 group-hover:text-amber-600 dark:group-hover:text-amber-400 transition-colors">{{ item.title }}</h3>
        <p class="text-slate-600 dark:text-slate-400 text-sm leading-relaxed">{{ item.desc }}</p>

        <div class="mt-6 flex items-center gap-2 text-amber-600/0 group-hover:text-amber-600 transition-colors text-sm font-bold">
          <span>Baca Selengkapnya</span>
          <svg class="w-4 h-4 transform group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
        </div>
      </div>
    </div>

    <transition name="modal">
      <div v-if="activeDetail" class="fixed inset-0 z-50 flex items-center justify-center p-4">
        <div class="absolute inset-0 bg-white/80 dark:bg-slate-950/80 backdrop-blur-xl" @click="closeDetail"></div>
        
        <div class="relative w-full max-w-2xl glass-panel p-8 md:p-12 shadow-2xl rounded-3xl z-10 transform transition-all text-center">
          <div class="w-24 h-24 mx-auto rounded-3xl bg-gradient-to-br from-white to-gray-200 flex items-center justify-center mb-8 shadow-xl">
            <svg class="w-12 h-12 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24" v-html="activeDetail.icon"></svg>
          </div>
          
          <h3 class="text-3xl font-bold text-slate-900 dark:text-white mb-4">{{ activeDetail.title }}</h3>
          <div class="w-16 h-1 bg-amber-500 mx-auto mb-6 rounded-full"></div>
          <p class="text-slate-700 dark:text-slate-300 text-lg leading-relaxed mb-10">
            {{ activeDetail.details }}
          </p>
          
          <button @click="closeDetail" class="px-8 py-3 rounded-xl bg-amber-500 hover:bg-amber-600 text-white font-bold transition-colors shadow-lg shadow-amber-500/20">
            Tutup
          </button>
        </div>
      </div>
    </transition>
  </section>
</template>
<style scoped>
@keyframes shimmer {
  100% { transform: translateX(100%); }
}
.modal-enter-active,
.modal-leave-active {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: scale(0.9) translateY(30px);
}
</style>