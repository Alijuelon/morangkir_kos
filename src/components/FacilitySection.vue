<script setup>
import { ref } from 'vue'

const facilities = ref([
  { 
    // SVG Ikon Kamar (Door/Room)
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6" />`, 
    title: 'Kamar Luas', 
    desc: 'Ruangan lega dengan sirkulasi udara optimal.',
    details: 'Setiap kamar didesain dengan ukuran yang ideal untuk memberikan ruang gerak maksimal. Dilengkapi dengan jendela yang memastikan cahaya matahari dan sirkulasi udara segar masuk dengan baik.'
  },
  { 
    // SVG Ikon Tempat Tidur
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z" />`, 
    title: 'Tempat Tidur Nyaman', 
    desc: 'Kasur empuk siap pakai untuk istirahat Anda.',
    details: 'Tersedia tempat tidur berkualitas lengkap dengan kasur busa/springbed yang empuk, bantal, dan seprai bersih. Siap memberikan kualitas tidur terbaik setelah seharian beraktivitas.'
  },
  { 
    // SVG Ikon Meja (Desktop/Desk)
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />`, 
    title: 'Meja Kerja/Belajar', 
    desc: 'Area produktif di dalam kamar.',
    details: 'Fasilitas meja kerja fungsional dengan ukuran proporsional. Sangat cocok bagi Anda yang bekerja dari rumah (WFH) atau membutuhkan area khusus untuk membuka laptop dan merapikan dokumen.'
  },
  { 
    // SVG Ikon Kursi (Chair - menggunakan representasi user sitting/office chair)
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />`, 
    title: 'Kursi Ergonomis', 
    desc: 'Pasangan meja untuk kenyamanan bekerja.',
    details: 'Kursi yang disediakan dirancang untuk menopang postur tubuh dengan baik saat Anda duduk di meja, memastikan kenyamanan meski digunakan dalam waktu yang lama.'
  },
  { 
    // SVG Ikon Lemari (Archive/Cabinet)
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 8h14M5 8a2 2 0 110-4h14a2 2 0 110 4M5 8v10a2 2 0 002 2h10a2 2 0 002-2V8m-9 4h4" />`, 
    title: 'Lemari Pakaian', 
    desc: 'Tempat penyimpanan barang yang aman dan luas.',
    details: 'Lemari pakaian kayu berkapasitas besar dengan area gantungan baju dan rak tumpuk. Cukup untuk menyimpan pakaian kerja, koper, dan barang-barang pribadi Anda lainnya.'
  },
  { 
    // SVG Ikon Dapur (Fire/Cooking)
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 18.657A8 8 0 016.343 7.343S7 9 9 10c0-2 .5-5 2.986-7C14 5 16.09 5.777 17.656 7.343A7.975 7.975 0 0120 13a7.975 7.975 0 01-2.343 5.657z" />`, 
    title: 'Dapur Bersama', 
    desc: 'Area memasak lengkap dan bersih.',
    details: 'Dapur umum yang dapat digunakan kapan saja. Terdapat kompor, wastafel cuci piring, dan ruang sirkulasi yang baik untuk mencegah bau masakan masuk ke area kamar.'
  },
  { 
    // SVG Ikon WiFi
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8.111 16.404a5.5 5.5 0 017.778 0M12 20h.01m-7.08-7.071c3.904-3.905 10.236-3.905 11.414 0M4.222 9.192a11.002 11.002 0 0115.556 0" />`, 
    title: 'Free WiFi', 
    desc: 'Internet stabil tanpa batas kuota.',
    details: 'Nikmati akses internet nirkabel (WiFi) berkecepatan tinggi yang tersedia 24 jam secara gratis. Cocok untuk keperluan streaming, media sosial, atau pekerjaan jarak jauh.'
  },
  { 
    // SVG Ikon CCTV (Video Camera)
    icon: `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 10l4.553-2.276A1 1 0 0121 8.618v6.764a1 1 0 01-1.447.894L15 14M5 18h8a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v8a2 2 0 002 2z" />`, 
    title: 'CCTV 24 Jam', 
    desc: 'Keamanan terpantau setiap saat.',
    details: 'Sistem keamanan kos diawasi ketat melalui kamera CCTV yang merekam 24/7. Ditempatkan di area strategis seperti pintu masuk, parkiran, dan lorong utama untuk menjamin ketenangan Anda.'
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
      <h2 class="text-4xl md:text-5xl font-bold mb-4 text-slate-900 dark:text-white">Fasilitas <span class="text-gold">Morangkir_Kos</span></h2>
      <p class="text-slate-600 dark:text-slate-400">Pilih fasilitas di bawah ini untuk melihat detail lengkapnya.</p>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 max-w-7xl mx-auto px-4 relative z-10">
      <div v-for="(item, index) in facilities" :key="index" @click="openDetail(item)" class="glass-card p-6 group cursor-pointer">
        <div class="absolute inset-0 -translate-x-full bg-gradient-to-r from-transparent via-white/40 dark:via-white/10 to-transparent group-hover:animate-[shimmer_1.5s_infinite] skew-x-12"></div>
        
        <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-white to-gray-200 shadow-[0_0_20px_rgba(0,0,0,0.1)] dark:shadow-[0_0_20px_rgba(255,255,255,0.15)] flex items-center justify-center mb-5 transform transition-transform duration-500 group-hover:scale-110 group-hover:rotate-6">
          <svg class="w-7 h-7 text-black drop-shadow-md" fill="none" stroke="currentColor" viewBox="0 0 24 24" v-html="item.icon"></svg>
        </div>
        
        <h3 class="text-xl font-bold text-slate-900 dark:text-white mb-2 group-hover:text-amber-600 dark:group-hover:text-amber-400 transition-colors">{{ item.title }}</h3>
        <p class="text-slate-600 dark:text-slate-400 text-xs leading-relaxed">{{ item.desc }}</p>

        <div class="mt-4 flex items-center gap-2 text-amber-600/0 group-hover:text-amber-600 transition-colors text-xs font-bold">
          <span>Baca Selengkapnya</span>
          <svg class="w-3 h-3 transform group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
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