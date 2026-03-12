<script setup>
import { ref } from 'vue'
import depan from '../assets/images/depan.jpeg'
import tempatTidur from '../assets/images/tempatTidur.jpeg'
import fasilitas from '../assets/images/fasilitas.jpeg'
import kamarMandi from '../assets/images/kamarMandi.jpeg'
import dapur from '../assets/images/dapur.jpeg'

const photos = ref([
  {
    id: 1,
    title: 'Tampak Depan',
    url: depan,
    desc: 'Tampak depan modern dengan pencahayaan hangat dan keamanan 24 jam.',
    details: 'Bangunan 1 lantai dengan arsitektur kontemporer. Dilengkapi dengan akses key door, CCTV, dan area parkir yang cukup untuk kendaran roda dua. Pencahayaan malam dirancang khusus untuk memberikan kesan hangat dan menyambut setiap penghuni yang pulang bekerja.'
  },
  {
    id: 2,
    title: 'Interior Kamar',
    url: tempatTidur,
    desc: 'Ruang istirahat lega.',
    details: 'Setiap kamar didesain untuk kenyamanan yang baik. Dilengkapi tempat tidur, AC, Meja Kerja, Lemari Pakaian, dan jendela untuk sirkulasi udara optimal.'
  },
  {
    id: 3,
    title: 'Kamar Mandi Dalam',
    url: kamarMandi,
    desc: 'Bersih dan lengkap.',
    details: 'Kamar mandi privat di dalam kamar.'
  },
  {
    id: 4,
    title: 'Area Dapur',
    url: dapur,
    desc: 'Dapur bersama yang bersih .',
    details: 'Area yang nyaman untuk memasak. Terdapat washtafel.'
  },
  {
    id: 5,
    title: 'Fasilitas dalam kamar',
    url: fasilitas,
    desc: 'Area untuk bersantai dan istrahat.',
    details: 'Setiap kamar didesain untuk kenyamanan yang baik. Dilengkapi tempat tidur, AC, Meja Kerja, Lemari Pakaian, dan jendela untuk sirkulasi udara optimal.'
  },
])

const activeModal = ref(null)
const cardRefs = ref([])

// Efek 3D Tilt untuk kartu galeri
const handleMouseMove = (e, index) => {
  const card = cardRefs.value[index]
  if (!card) return

  const rect = card.getBoundingClientRect()
  const x = e.clientX - rect.left 
  const y = e.clientY - rect.top  
  
  const centerX = rect.width / 2
  const centerY = rect.height / 2
  
  const rotateX = ((y - centerY) / centerY) * -10
  const rotateY = ((x - centerX) / centerX) * 10

  card.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale3d(1.02, 1.02, 1.02)`
}

const handleMouseLeave = (index) => {
  const card = cardRefs.value[index]
  if (!card) return
  card.style.transform = `perspective(1000px) rotateX(0deg) rotateY(0deg) scale3d(1, 1, 1)`
}

const openModal = (photo) => {
  activeModal.value = photo
  document.body.style.overflow = 'hidden' // Mencegah scroll saat modal terbuka
}

const closeModal = () => {
  activeModal.value = null
  document.body.style.overflow = 'auto' // Mengembalikan scroll
}
</script>

<template>
  <section class="py-24 overflow-hidden relative">
    <div class="text-center mb-16 relative z-10">
     <h2 class="text-4xl md:text-5xl font-bold mb-4 text-slate-900 dark:text-white">Eksplorasi <span class="text-gold">Morangkir_Kos</span></h2>
<p class="text-slate-600 dark:text-slate-400 max-w-2xl mx-auto">Klik gambar untuk melihat detail ruangan lebih jelas.</p>
    </div>

    <div class="flex justify-center gap-8 flex-wrap px-4 max-w-7xl mx-auto">
      <div 
        v-for="(photo, index) in photos" 
        :key="photo.id"
        class="relative w-full md:w-[calc(50%-2rem)] lg:w-[calc(33.333%-2rem)] h-80 group"
      >
        <div
          :ref="el => { if (el) cardRefs[index] = el }"
          @mousemove="handleMouseMove($event, index)"
          @mouseleave="handleMouseLeave(index)"
          @click="openModal(photo)"
          class="w-full h-full transition-transform duration-300 ease-out cursor-pointer"
          style="transform-style: preserve-3d;"
        >
          <div class="absolute inset-0 rounded-3xl overflow-hidden glass-panel border border-white/10 shadow-xl group-hover:shadow-amber-500/20">
            <div class="absolute inset-0 bg-gradient-to-t from-slate-950 via-slate-900/40 to-transparent z-10 group-hover:via-slate-900/20 transition-all duration-500"></div>
            
            <img :src="photo.url" :alt="photo.title" class="w-full h-full object-cover transition-transform duration-1000 group-hover:scale-110" />
            
            <div class="absolute bottom-6 left-6 right-6 z-20 transform translate-z-10">
              <div class="inline-flex items-center gap-2 px-3 py-1 mb-3 rounded-full bg-black/40 backdrop-blur-md border border-white/20 text-xs text-amber-400 font-medium group-hover:bg-amber-500/20 transition-colors">
                <span>Lihat Detail</span>
                <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"></path></svg>
              </div>
              <h3 class="text-2xl font-bold text-white mb-1 drop-shadow-lg">{{ photo.title }}</h3>
            </div>
          </div>
        </div>
      </div>
    </div>

    <transition name="modal">
      <div v-if="activeModal" class="fixed inset-0 z-50 flex items-center justify-center p-4 sm:p-6 md:p-12">
        <div class="absolute inset-0 bg-slate-950/80 backdrop-blur-xl" @click="closeModal"></div>
        
        <div class="relative w-full max-w-6xl max-h-[90vh] glass-panel bg-white/5 border border-white/20 shadow-[0_20px_60px_-15px_rgba(245,158,11,0.3)] flex flex-col md:flex-row overflow-hidden rounded-3xl z-10 transform transition-all">
          
          <button @click="closeModal" class="absolute top-4 right-4 z-20 w-10 h-10 rounded-full bg-black/50 hover:bg-amber-500 text-white flex items-center justify-center transition-colors backdrop-blur-md border border-white/10">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
          </button>

          <div class="w-full md:w-3/5 h-64 md:h-auto relative">
            <img :src="activeModal.url" :alt="activeModal.title" class="w-full h-full object-cover" />
            <div class="absolute inset-0 bg-gradient-to-r from-transparent to-slate-900/90 hidden md:block"></div>
            <div class="absolute inset-0 bg-gradient-to-t from-slate-900/90 to-transparent block md:hidden"></div>
          </div>

          <div class="w-full md:w-2/5 p-8 md:p-12 flex flex-col justify-center overflow-y-auto">
            <h3 class="text-4xl font-bold text-white mb-2">{{ activeModal.title }}</h3>
            <p class="text-amber-400 font-medium mb-8 text-lg">{{ activeModal.desc }}</p>
            
            <div class="space-y-4">
              <h4 class="text-sm tracking-widest text-slate-400 uppercase font-bold">Informasi Detail:</h4>
              <p class="text-slate-300 leading-relaxed text-lg">
                {{ activeModal.details }}
              </p>
            </div>
            
            <button @click="closeModal" class="mt-10 px-6 py-3 rounded-xl border border-amber-500/50 text-amber-400 hover:bg-amber-500 hover:text-white transition-colors font-semibold self-start">
              Tutup Detail
            </button>
          </div>

        </div>
      </div>
    </transition>
  </section>
</template>

<style scoped>
/* Transisi mulus untuk Modal */
.modal-enter-active,
.modal-leave-active {
  transition: all 0.4s ease;
}
.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: scale(0.95) translateY(20px);
}
</style>