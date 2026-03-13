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
    desc: 'Tampak depan bangunan dengan keamanan 24 jam.',
    details: 'Akses kunci khusus, pengawasan CCTV, dan parkir motor.'
  },
  {
    id: 2,
    title: 'Interior Kamar',
    url: tempatTidur,
    desc: 'Ruang istirahat yang nyaman.',
    details: 'Lengkap dengan kasur, AC, meja kerja, dan lemari pakaian.'
  },
  {
    id: 3,
    title: 'Kamar Mandi Dalam',
    url: kamarMandi,
    desc: 'Bersih dan rapi.',
    details: 'Fasilitas kamar mandi privat di setiap kamar.'
  },
  {
    id: 4,
    title: 'Area Dapur',
    url: dapur,
    desc: 'Dapur bersama yang bersih.',
    details: 'Area memasak komunal dengan wastafel cuci piring.'
  },
  {
    id: 5,
    title: 'Fasilitas Kamar',
    url: fasilitas,
    desc: 'Area istirahat fungsional.',
    details: 'Kamar siap huni dengan furnitur dasar lengkap.'
  },
])

const activeModal = ref(null)
const cardRefs = ref([])
const showInfo = ref(false)

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
  showInfo.value = false 
  document.documentElement.style.overflow = 'hidden' // Kunci scroll halaman belakang
}

const closeModal = () => {
  activeModal.value = null
  showInfo.value = false
  document.documentElement.style.overflow = 'auto' // Kembalikan scroll
}
</script>

<template>
  <section class="py-24 overflow-hidden relative" id="galeri">
    <div class="text-center mb-16 relative z-10">
     <h2 class="text-4xl md:text-5xl font-bold mb-4 text-slate-900 dark:text-white">Galeri <span class="text-gold">Kos</span></h2>
     <p class="text-slate-600 dark:text-slate-400 max-w-2xl mx-auto">Klik gambar untuk melihat detail.</p>
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
          <div class="absolute inset-0 rounded-3xl overflow-hidden glass-panel border border-white/10 shadow-xl group-hover:shadow-amber-500/20 transition-all duration-500">
            <div class="absolute inset-0 bg-gradient-to-t from-slate-950 via-slate-900/40 to-transparent z-10 group-hover:via-slate-900/20 transition-all duration-500"></div>
            
            <img :src="photo.url" :alt="photo.title" class="w-full h-full object-cover transition-transform duration-1000 group-hover:scale-110" />
            
            <div class="absolute bottom-6 left-6 right-6 z-20 transform translate-z-10">
              <div class="inline-flex items-center gap-2 px-3 py-1 mb-3 rounded-full bg-black/40 backdrop-blur-md border border-white/20 text-xs text-amber-400 font-medium group-hover:bg-amber-500/20 transition-colors">
                <span>Lihat Foto</span>
              </div>
              <h3 class="text-2xl font-bold text-white mb-1 drop-shadow-lg">{{ photo.title }}</h3>
            </div>
          </div>
        </div>
      </div>
    </div>

    <Teleport to="body">
      <transition name="modal-smooth">
        <div v-if="activeModal" class="fixed inset-0 z-[99999] flex items-center justify-center p-4 w-screen h-screen">
          
          <div class="absolute inset-0 bg-black/95 backdrop-blur-md" @click="closeModal"></div>

          <div class="modal-content-smooth relative w-full max-w-4xl max-h-[90vh] flex items-center justify-center z-10 pointer-events-none">
            
            <div class="relative bg-black rounded-2xl border border-white/10 shadow-2xl overflow-hidden flex flex-col items-center pointer-events-auto">
              
              <img 
                :src="activeModal.url" 
                :alt="activeModal.title" 
                class="w-auto h-auto max-w-full max-h-[85vh] object-contain block"
              />

              <div class="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-t from-black/90 to-transparent pointer-events-none z-10"></div>

              <div class="absolute bottom-4 left-0 right-0 flex items-center justify-center gap-4 z-40 px-4">
                
                <button 
                  @click="showInfo = !showInfo" 
                  class="px-5 py-2.5 rounded-full bg-white/10 hover:bg-white/20 text-white backdrop-blur-md border border-white/20 transition-colors text-sm font-medium flex items-center gap-2 shadow-lg"
                >
                  <svg class="w-4 h-4 text-amber-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                  {{ showInfo ? 'Sembunyikan Info' : 'Info Ruangan' }}
                </button>

                <button 
                  @click="closeModal" 
                  class="px-6 py-2.5 rounded-full bg-amber-500 hover:bg-amber-600 text-white transition-colors text-sm font-bold shadow-lg shadow-amber-500/30"
                >
                  Tutup
                </button>
                
              </div>

              <transition name="fade-up">
                <div v-if="showInfo" class="absolute inset-x-0 bottom-0 bg-black/85 backdrop-blur-md p-6 pt-8 pb-20 z-30 border-t border-white/10 text-center">
                  <h3 class="text-xl md:text-2xl font-bold text-white mb-1">{{ activeModal.title }}</h3>
                  <p class="text-amber-400 text-sm font-medium mb-3">{{ activeModal.desc }}</p>
                  <div class="h-[1px] w-1/3 mx-auto bg-white/20 mb-3"></div>
                  <p class="text-slate-200 text-sm leading-relaxed max-w-xl mx-auto">
                    {{ activeModal.details }}
                  </p>
                </div>
              </transition>

            </div>
          </div>

        </div>
      </transition>
    </Teleport>
  </section>
</template>

<style scoped>
/* Transisi Smooth Mulus (Fade & Sedikit Scale) */
.modal-smooth-enter-active,
.modal-smooth-leave-active {
  transition: all 0.3s ease-out;
}
.modal-smooth-enter-from,
.modal-smooth-leave-to {
  opacity: 0;
}
.modal-smooth-enter-from .modal-content-smooth,
.modal-smooth-leave-to .modal-content-smooth {
  transform: scale(0.96) translateY(10px);
}

/* Transisi Overlay Teks (Meluncur dari bawah) */
.fade-up-enter-active,
.fade-up-leave-active {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
.fade-up-enter-from,
.fade-up-leave-to {
  opacity: 0;
  transform: translateY(20px);
}
</style>