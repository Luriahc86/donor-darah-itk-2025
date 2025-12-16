<template>
  <section class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-10">
    <h1 class="text-2xl font-semibold mb-6">Kampanye Donor Darah</h1>

    <div class="grid md:grid-cols-4 gap-4 mb-6">
      <SummaryCard label="Event Mendatang" value="4" color="bg-red-50"/>
      <SummaryCard label="Sedang Berlangsung" value="1" color="bg-green-50"/>
      <SummaryCard label="Telah Selesai" value="3" color="bg-blue-50"/>
      <SummaryCard label="Total Peserta" value="1069" color="bg-gray-50"/>
    </div>

    <div class="flex gap-2 mb-6">
      <button class="filter-btn">Semua Event</button>
      <button class="filter-btn">Akan Datang</button>
      <button class="filter-btn">Berlangsung</button>
      <button class="filter-btn">Selesai</button>
    </div>

    <h3 class="font-semibold mb-3">Sedang Berlangsung</h3>
    <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-3 mb-8">
     <div data-aos="fade-left">
      <img
        :src="kampanyeImage2"
        alt="Tentang Kami"
        class="rounded-2xl w-full h-[320px] object-cover shadow-lg hover:scale-105 transition-transform duration-500"
      />
    </div>
    </div>

    <h3 class="font-semibold mb-3">Akan Datang</h3>
    <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-3">
      <div data-aos="fade-left">
      <img
        :src="kampanyeImage"
        alt="Tentang Kami"
        class="rounded-2xl w-full h-[320px] object-cover shadow-lg hover:scale-105 transition-transform duration-500"
      />
    </div>
      <div data-aos="fade-left">
      <img
        :src="kampanyeImage2"
        alt="Tentang Kami"
        class="rounded-2xl w-full h-[320px] object-cover shadow-lg hover:scale-105 transition-transform duration-500"
      />
    </div>

    </div>

    <div class="mt-10 rounded-2xl p-8 text-center text-white bg-gradient-to-r from-red-600 to-red-500">
      <p class="mb-3">Tidak menemukan event yang sesuai?</p>

      <a
        href="mailto:info@donorkampus.id?subject=Konsultasi%20Event%20Donor%20Darah&body=Halo%20Panitia%20Kampanye%20Donor%20Darah%2C%0D%0A%0D%0ASaya%20ingin%20bertanya%20mengenai%20event%20donor..."
        class="inline-block px-4 py-2 rounded-lg bg-white text-red-600 hover:bg-red-50"
      >
        Hubungi Panitia Kampus
      </a>
    </div>
  </section>
</template>

<script setup>
import kampanyeImage from '../assets/kampanye.jpeg';
import kampanyeImage2 from '../assets/kampanye_2.jpeg';

const SummaryCard = (props) => null
const EventCard = (props) => null
</script>

<style scoped>
.filter-btn {
  @apply px-3 py-1 rounded-lg border bg-white text-gray-800 hover:bg-gray-100 transition;
}
</style>
