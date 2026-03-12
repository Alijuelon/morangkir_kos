<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const isMenuOpen = ref(false)
const isDark = ref(true) // Default kita buat dark mode agar kesan mewahnya langsung terasa

// Fungsi mendeteksi scroll
const handleScroll = () => {
  isScrolled.value = window.scrollY > 20
}

// Fungsi ganti tema (Dark/Light Mode)
const toggleTheme = () => {
  isDark.value = !isDark.value
  if (isDark.value) {
    document.documentElement.classList.add('dark')
    localStorage.setItem('theme', 'dark')
  } else {
    document.documentElement.classList.remove('dark')
    localStorage.setItem('theme', 'light')
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  
  // Cek tema terakhir yang dipilih user dari Local Storage
  const savedTheme = localStorage.getItem('theme')
  if (savedTheme === 'light') {
    isDark.value = false
    document.documentElement.classList.remove('dark')
  } else {
    document.documentElement.classList.add('dark')
  }
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

const navLinks = [
  { name: 'Beranda', href: '#' },
  { name: 'Galeri', href: '#galeri' },
  { name: 'Fasilitas', href: '#fasilitas' },
  { name: 'Kontak', href: '#contact' }
]
</script>

<template>
  <nav 
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-500',
      isScrolled ? 'py-4' : 'py-6'
    ]"
  >
    <div 
      :class="[
        'container mx-auto px-6 max-w-7xl transition-all duration-500 rounded-3xl',
        isScrolled ? 'glass-panel !rounded-full shadow-lg border-white/20 bg-white/10 dark:bg-black/20 backdrop-blur-2xl' : ''
      ]"
    >
      <div class="flex items-center justify-between">
        
        <a href="#" class="text-2xl font-bold tracking-tight">
          <span class="text-gold">Morangkir</span>
          <span class="text-slate-800 dark:text-white transition-colors">_Kos</span>
        </a>

        <div class="hidden md:flex items-center gap-8">
          <a 
            v-for="link in navLinks" 
            :key="link.name" 
            :href="link.href"
            class="text-sm font-medium text-slate-600 hover:text-amber-500 dark:text-slate-300 dark:hover:text-amber-400 transition-colors"
          >
            {{ link.name }}
          </a>
          
          <button 
            @click="toggleTheme" 
            class="p-2 rounded-full glass-card !shadow-none border border-black/10 dark:border-white/10 hover:scale-110 transition-transform flex items-center justify-center bg-white/50 dark:bg-white/5"
            aria-label="Toggle Dark Mode"
          >
            <svg v-if="!isDark" class="w-5 h-5 text-slate-800" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"></path></svg>
            <svg v-else class="w-5 h-5 text-amber-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"></path></svg>
          </button>
        </div>

        <div class="flex md:hidden items-center gap-4">
          <button @click="toggleTheme" class="p-2 rounded-full glass-card !shadow-none border border-black/10 dark:border-white/10">
            <svg v-if="!isDark" class="w-5 h-5 text-slate-800" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"></path></svg>
            <svg v-else class="w-5 h-5 text-amber-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"></path></svg>
          </button>
          
          <button @click="isMenuOpen = !isMenuOpen" class="text-slate-800 dark:text-white focus:outline-none">
            <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
              <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
            </svg>
          </button>
        </div>
      </div>

      <transition
        enter-active-class="transition duration-300 ease-out"
        enter-from-class="transform -translate-y-4 opacity-0"
        enter-to-class="transform translate-y-0 opacity-100"
        leave-active-class="transition duration-200 ease-in"
        leave-from-class="transform translate-y-0 opacity-100"
        leave-to-class="transform -translate-y-4 opacity-0"
      >
        <div v-if="isMenuOpen" class="md:hidden pt-4 pb-2 absolute top-full left-4 right-4 mt-2 glass-panel bg-white/80 dark:bg-black/80 backdrop-blur-xl border-black/10 dark:border-white/10 rounded-2xl shadow-2xl">
          <div class="flex flex-col space-y-4 p-4 text-center">
            <a 
              v-for="link in navLinks" 
              :key="link.name" 
              :href="link.href"
              @click="isMenuOpen = false"
              class="text-lg font-medium text-slate-800 dark:text-slate-200 hover:text-amber-500 dark:hover:text-amber-400 transition-colors"
            >
              {{ link.name }}
            </a>
          </div>
        </div>
      </transition>
    </div>
  </nav>
</template>