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
                  Jl.Lembaga, Gg.Ibrahim, Senggoro, Bengkalis, Riau
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
                  +62-853-6548-8875
                </p>

              </div>

            </div>

          </div>

          <!-- BUTTON WHATSAPP -->
          <a
            href="https://wa.me/+6285365488875"
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
  src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3988.342371926619!2d102.133221!3d1.448556!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x31d15fc32c1c3f2d%3A0x6d9f7a77e0c4a6a!2sJl.%20Lembaga%2C%20Senggoro%2C%20Kec.%20Bengkalis%2C%20Kabupaten%20Bengkalis%2C%20Riau!5e0!3m2!1sid!2sid!4v1709500000000!5m2!1sid!2sid"
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