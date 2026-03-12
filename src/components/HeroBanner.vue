<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import depan from '../assets/images/depan.jpeg'
import fasilitas from '../assets/images/fasilitas.jpeg'
// Menyimpan posisi mouse untuk efek Parallax 3D
const mouseX = ref(0)
const mouseY = ref(0)
const isHovering = ref(false)

const handleMouseMove = (e) => {
  // Mengonversi posisi mouse menjadi nilai dari -1 hingga 1
  mouseX.value = (e.clientX / window.innerWidth - 0.5) * 2
  mouseY.value = (e.clientY / window.innerHeight - 0.5) * 2
}

onMounted(() => {
  window.addEventListener('mousemove', handleMouseMove)
})

onUnmounted(() => {
  window.removeEventListener('mousemove', handleMouseMove)
})
</script>
<template>
  <section class="relative min-h-[90vh] flex items-center pt-20 pb-10 overflow-hidden">
    
    <div class="absolute inset-0 pointer-events-none z-0">
      <div class="absolute top-20 left-10 w-72 h-72 bg-amber-500/20 rounded-full blur-[100px] animate-pulse"></div>
      <div class="absolute bottom-10 right-20 w-96 h-96 bg-blue-600/10 rounded-full blur-[120px] animate-pulse" style="animation-delay: 2s;"></div>
    </div>

    <div class="container mx-auto px-4 relative z-10 flex flex-col lg:flex-row items-center gap-16">
      
      <div class="flex-1 w-full flex flex-col items-center lg:items-start text-center lg:text-left space-y-8 animate-fade-in-up">
        
        <div class="inline-flex items-center gap-2 px-5 py-2 rounded-full glass-panel border border-amber-500/30 bg-white/5 backdrop-blur-md text-amber-600 dark:text-amber-400 text-sm font-bold tracking-wide shadow-[0_0_20px_rgba(245,158,11,0.15)] animate-[float_4s_ease-in-out_infinite]">
          <span class="relative flex h-3 w-3">
            <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-amber-400 opacity-75"></span>
            <span class="relative inline-flex rounded-full h-3 w-3 bg-amber-500"></span>
          </span>
          Hunian Nyaman #1 
        </div>

        <h1 class="text-5xl sm:text-6xl md:text-7xl font-extrabold leading-[1.1] tracking-tight text-slate-900 dark:text-white">
          Tingkatkan <br />
          Kualitas Hidup di <br />
          <span class="relative inline-block mt-2">
            <span class="text-gold relative z-10">Morangkir_Kos</span>
            <span class="absolute bottom-2 left-0 w-full h-3 bg-amber-500/30 blur-md -z-10"></span>
          </span>
        </h1>

        <p class="text-lg md:text-xl text-slate-600 dark:text-slate-300 max-w-xl leading-relaxed font-light">
          Definisi baru dari kenyamanan kos eksklusif. Desain arsitektur modern, privasi maksimal, dan fasilitas setara apartemen premium untuk profesional muda.
        </p>

        <div class="flex flex-col sm:flex-row gap-5 pt-4 w-full justify-center lg:justify-start">
          <a href="#contact" class="group relative px-8 py-4 rounded-2xl bg-gradient-to-r from-amber-500 to-amber-600 text-white font-bold text-lg overflow-hidden transition-all duration-300 hover:scale-105 hover:shadow-[0_0_40px_rgba(245,158,11,0.4)]">
            <div class="absolute inset-0 bg-white/20 translate-y-full group-hover:translate-y-0 transition-transform duration-300 ease-out"></div>
            <span class="relative z-10 flex items-center gap-2">
              Booking Kamar
              <svg class="w-5 h-5 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
            </span>
          </a>
          
          <a href="#fasilitas" class="px-8 py-4 rounded-2xl border border-slate-300 dark:border-white/20 glass-panel hover:bg-slate-200 dark:hover:bg-white/10 hover:border-slate-400 dark:hover:border-white/40 text-slate-800 dark:text-white font-bold text-lg transition-all duration-300 hover:scale-105 flex items-center gap-2">
            <span>Lihat Fasilitas</span>
          </a>
        </div>
      </div>

      <div class="flex-1 w-full h-[500px] relative perspective-1000" @mouseenter="isHovering = true" @mouseleave="isHovering = false">
        <div class="w-full h-full relative transform-style-3d transition-transform duration-700 ease-out" :style="{ transform: isHovering ? `rotateX(${mouseY * -10}deg) rotateY(${mouseX * 10}deg)` : 'rotateX(0deg) rotateY(0deg)' }">
          
          <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-80 h-80 rounded-full border-[10px] border-slate-200 dark:border-white/5 shadow-[0_0_50px_rgba(0,0,0,0.05)] dark:shadow-[0_0_50px_rgba(255,255,255,0.05)] transform-style-3d animate-[spin_20s_linear_infinite]" style="transform: translateZ(-100px) rotateX(45deg);"></div>

          <div class="absolute top-10 right-0 w-3/4 h-80 glass-panel p-2 shadow-2xl transition-transform duration-500 ease-out" :style="{ transform: `translateZ(20px) translateX(${mouseX * -20}px) translateY(${mouseY * -20}px)` }">
            <div class="w-full h-full rounded-2xl overflow-hidden relative">
              <div class="absolute inset-0 bg-amber-500/20 mix-blend-overlay z-10"></div>
              <img src="../assets/images/tempatTidur.jpeg" alt="Fasad" class="w-full h-full object-cover" />
            </div>
          </div>

          <div class="absolute bottom-0 left-0 w-2/3 h-64 glass-card p-2 shadow-2xl border-white/20 transition-transform duration-500 ease-out" :style="{ transform: `translateZ(60px) translateX(${mouseX * 30}px) translateY(${mouseY * 30}px)` }">
            <div class="w-full h-full rounded-xl overflow-hidden relative">
              <img src="../assets/images/depan.jpeg" alt="Interior" class="w-full h-full object-cover" />
              <div class="absolute bottom-0 w-full p-4 bg-gradient-to-t from-black/80 to-transparent">
                <p class="text-white font-semibold text-lg drop-shadow-md">Kamar Suite Premium</p>
              </div>
            </div>
          </div>

          <div class="absolute top-20 left-10 p-4 rounded-2xl glass-panel border border-amber-500/40 bg-white/80 dark:bg-black/40 backdrop-blur-xl shadow-2xl transition-transform duration-500 ease-out flex items-center gap-4" :style="{ transform: `translateZ(100px) translateX(${mouseX * 50}px) translateY(${mouseY * 50}px)` }">
            <div class="w-12 h-12 rounded-full bg-gradient-to-br from-amber-400 to-amber-600 flex items-center justify-center text-white font-bold text-xl shadow-lg">5.0</div>
            <div>
              <div class="flex text-amber-500 text-sm">★★★★★</div>
              <p class="text-slate-800 dark:text-white text-xs font-bold mt-1">Review Penghuni</p>
            </div>
          </div>

        </div>
      </div>

    </div>
  </section>
</template>
<style scoped>
.perspective-1000 {
  perspective: 1000px;
}
.transform-style-3d {
  transform-style: preserve-3d;
}

/* Animasi masuk berurutan untuk teks */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
.animate-fade-in-up {
  animation: fadeInUp 1s ease-out forwards;
}
</style>