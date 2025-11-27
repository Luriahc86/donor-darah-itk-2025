<template>
  <section class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 py-10">
    <h1 class="text-2xl font-semibold mb-6">Permintaan Darah</h1>

    <div class="grid md:grid-cols-3 gap-4 mb-6">
      <InfoCard title="Cepat & Mudah" desc="Proses pengajuan sekitar 5 menit."/>
      <InfoCard title="Respon 24/7" desc="Tim siap membantu kapan saja."/>
      <InfoCard title="Stok Terjamin" desc="Ketersediaan darah aman dan terpantau."/>
    </div>

    <div class="mb-6 grid md:grid-cols-2 gap-3">
      <button class="border rounded-xl p-4 flex items-start gap-3 bg-red-50">
        <span><b>Perorangan</b><br><small>Untuk kebutuhan pribadi/keluarga</small></span>
      </button>
      <button class="border rounded-xl p-4 flex items-start gap-3 bg-red-50">
        <span><b>Klinik ITK</b><br><small>Untuk institusi kesehatan</small></span>
      </button>
    </div>

    <form class="rounded-2xl border p-6 grid gap-4">
      <div class="grid md:grid-cols-2 gap-4">
        <div>
          <label class="text-sm">Nama Lengkap *</label>
          <input class="mt-1 input" placeholder="Nama Pemohon" v-model="nama" />
        </div>

        <div>
          <label class="text-sm">Golongan Darah yang Dibutuhkan *</label>
          <select class="mt-1 input" v-model="golongan">
            <option value="">-- Pilih --</option>
            <option>A+</option><option>A-</option><option>B+</option><option>B-</option>
            <option>O+</option><option>O-</option><option>AB+</option><option>AB-</option>
          </select>
        </div>

        <div>
          <label class="text-sm">Nomor Telepon *</label>
          <input class="mt-1 input" placeholder="08xx xxxx xxxx" v-model="telp" />
        </div>

        <div>
          <label class="text-sm">Email *</label>
          <input class="mt-1 input" type="email" placeholder="email@kampus.id" v-model="email" />
        </div>

        <div>
          <label class="text-sm">Tanggal Dibutuhkan *</label>
          <input class="mt-1 input" type="date" v-model="tanggal" />
        </div>

        <div>
          <label class="text-sm">Tingkat Urgensi *</label>
          <select class="mt-1 input" v-model="urgensi">
            <option value="">-- Pilih --</option>
            <option>Normal</option>
            <option>Segera</option>
            <option>Darurat</option>
          </select>
        </div>
      </div>

      <div>
        <label class="text-sm">Keterangan Tambahan</label>
        <textarea 
          class="mt-1 input" rows="4" 
          placeholder="Detail kondisi atau kebutuhan..."
          v-model="keterangan"
        ></textarea>
      </div>

      <p class="text-xs text-blue-700 bg-blue-50 border border-blue-200 p-3 rounded">
        <b>Catatan:</b> Pastikan data yang Anda masukkan benar. Tim kami akan menghubungi Anda untuk verifikasi.
      </p>

      <button 
        type="button"
        @click="submitForm"
        class="px-4 py-2 rounded-lg bg-red-600 text-white hover:bg-red-700"
      >
        Kirim Permintaan
      </button>
    </form>

    <div class="mt-6 rounded-xl border p-4 flex items-center justify-between">
      <div class="flex items-center gap-3">
        <span class="text-2xl">📞</span>
        <div>
          <div class="font-semibold">Butuh Bantuan Segera?</div>
          <div class="text-sm text-gray-600">Hotline 24/7 untuk kondisi darurat</div>
        </div>
      </div>
      <a href="tel:05421234567" class="px-4 py-2 rounded-lg bg-red-600 text-white">0542-123-4567</a>
    </div>

    <!-- TOAST NOTIFIKASI -->
    <div 
      v-if="showToast"
      :class="[
        'fixed bottom-6 right-6 px-4 py-3 rounded-lg shadow-lg animate-fade',
        toastType === 'error' ? 'bg-red-600 text-white' : 'bg-green-600 text-white'
      ]"
    >
      {{ toastMessage }}
    </div>

  </section>
</template>

<script setup>
import { ref } from "vue";

// toast state
const showToast = ref(false);
const toastMessage = ref("");
const toastType = ref("success"); // success | error

// form values
const nama = ref("");
const golongan = ref("");
const telp = ref("");
const email = ref("");
const tanggal = ref("");
const urgensi = ref("");
const keterangan = ref("");

function showNotification(message, type = "success") {
  toastMessage.value = message;
  toastType.value = type;
  showToast.value = true;

  setTimeout(() => {
    showToast.value = false;
  }, 3000);
}

function submitForm() {
  if (
    !nama.value ||
    !golongan.value ||
    !telp.value ||
    !email.value ||
    !tanggal.value ||
    !urgensi.value
  ) {
    return showNotification("Harap isi semua field yang wajib!", "error");
  }

  showNotification("Permintaan darah berhasil dikirim!", "success");
}
</script>

<style scoped>
.input { 
  @apply w-full rounded-lg border px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-300; 
}

@keyframes fade {
  0% { opacity: 0; transform: translateY(10px); }
  100% { opacity: 1; transform: translateY(0); }
}
.animate-fade { animation: fade 0.3s ease-out; }
</style>
