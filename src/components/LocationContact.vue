<template>
  <section id="contact" class="py-10 pb-24">
    <div class="glass-panel p-8 md:p-12">
      
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
        
        <!-- INFO KONTAK -->
        <div class="space-y-8">

          <div>
            <h2 class="text-4xl font-bold mb-2">
              Lokasi & <span class="text-gold">Kontak</span>
            </h2>

            <p class="text-slate-400">
              Posisinya strategis, dekat dengan area perkantoran dan fasilitas umum.
            </p>
          </div>

          <div class="space-y-6">

            <!-- ALAMAT -->
            <div class="flex items-start gap-4">
              
              <div
                class="w-12 h-12 rounded-full bg-amber-500/20 flex items-center justify-center text-amber-500 shrink-0"
              >
                📍
              </div>

              <div>
                <h4 class="font-bold text-lg">
                  Alamat Lengkap
                </h4>

                <p class="text-slate-400">
                  Jl. Contoh Mewah No. 123, Kawasan Sudirman,
                  Jakarta Selatan 12190
                </p>
              </div>

            </div>

            <!-- TELEPON -->
            <div class="flex items-start gap-4">

              <div
                class="w-12 h-12 rounded-full bg-amber-500/20 flex items-center justify-center text-amber-500 shrink-0"
              >
                📞
              </div>

              <div>

                <h4 class="font-bold text-lg">
                  Hubungi Pemilik
                </h4>

                <p class="text-slate-400">
                  Bpk.Monang Simorangkir
                </p>

                <p class="text-xl font-mono text-white mt-1">
                  085365488875
                </p>

              </div>

            </div>

          </div>

          <!-- BUTTON WHATSAPP -->
          <a
            href="https://wa.me/085365488875"
            target="_blank"
            rel="noopener"
            class="inline-flex items-center justify-center gap-3 w-full md:w-auto px-8 py-4 rounded-xl bg-green-500 hover:bg-green-600 text-white font-bold transition-colors shadow-lg shadow-green-500/20"
          >
            <span>Chat via WhatsApp</span>
          </a>

        </div>

        <!-- GOOGLE MAP -->
        <div
          class="relative h-[400px] rounded-2xl overflow-hidden border-2 border-white/10 shadow-2xl group"
        >

          <div
            class="absolute inset-0 bg-amber-500/20 mix-blend-overlay pointer-events-none z-10 group-hover:opacity-0 transition-opacity duration-500"
          ></div>

          <iframe
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3966.466738981442!2d106.8249641!3d-6.202024!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zNsKwMTInMDcuMyJTIDEwNsKwNDknMjkuOSJF!5e0!3m2!1sen!2sid!4v1620000000000!5m2!1sen!2sid"
            class="w-full h-full border-0 grayscale invert-[90%] contrast-[1.2] group-hover:grayscale-0 group-hover:invert-0 transition-all duration-700"
            loading="lazy"
            allowfullscreen
          ></iframe>

        </div>

      </div>

    </div>
  </section>
</template>

<script setup lang="ts">
// Komponen ini hanya tampilan statis
</script>

<style scoped>
.text-gold {
  color: #d4af37;
}

.glass-panel {
  background: rgba(15, 15, 15, 0.6);
  backdrop-filter: blur(12px);
  border-radius: 16px;
}
</style>