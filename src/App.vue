<script setup>
import Navbar from './components/Navbar.vue'
import HeroBanner from './components/HeroBanner.vue'
import PhotoGallery from './components/PhotoGallery.vue'
import FacilitySection from './components/FacilitySection.vue'
import LocationContact from './components/LocationContact.vue'
</script>

<template>
  <div class="relative min-h-screen transition-colors duration-700">
    
    <Navbar />

    <div class="fixed inset-0 z-0 overflow-hidden pointer-events-none transition-opacity duration-700">
      <div class="absolute top-[-10%] left-[-10%] w-96 h-96 bg-amber-500/30 dark:bg-amber-500/20 rounded-full blur-[120px] animate-pulse"></div>
      <div class="absolute bottom-[-10%] right-[-10%] w-[500px] h-[500px] bg-sky-400/20 dark:bg-blue-600/20 rounded-full blur-[150px]"></div>
      <div class="absolute top-[40%] left-[30%] w-[400px] h-[400px] bg-emerald-400/10 dark:bg-emerald-500/10 rounded-full blur-[130px] animate-pulse" style="animation-delay: 2s;"></div>
    </div>

    <main class="relative z-10 container mx-auto px-4 pt-16 pb-8 flex flex-col gap-24">
      <div id="home"><HeroBanner /></div>
      
      <div id="galeri"><PhotoGallery /></div>
      
      <FacilitySection />
      <LocationContact />
    </main>

    <footer class="relative z-10 py-6 text-center border-t border-black/10 dark:border-white/10 mt-12 glass-panel rounded-none bg-white/40 dark:bg-black/20">
      <p class="text-slate-600 dark:text-slate-400 text-sm">
        &copy; 2026 <span class="text-amber-500 font-semibold">Morangkir_Kos</span>. All rights reserved.
      </p>
    </footer>
  </div>
</template>

<style>
html {
  scroll-behavior: smooth; /* Membuat scroll dari Navbar lebih mulus */
}
html, body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}
</style>