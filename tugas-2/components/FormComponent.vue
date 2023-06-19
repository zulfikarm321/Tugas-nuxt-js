<script>
export default {
  data() {
    return {
      inputForm: {
        nik: '',
        nama: '',
        nilai: null,
      },
    }
  },
  methods: {
    formSubmit() {
      this.$emit('onSubmit', this.inputForm)
      this.inputForm = {
        nik: '',
        nama: '',
        nilai: null,
      }
    },
  },
}
</script>

<template>
  <form class="flex flex-col gap-3" @submit.prevent="formSubmit">
    <h1 class="text-xl font-bold text-center">Input Data Siswa</h1>
    <div class="input-field flex flex-col gap-2">
      <label for="nik" class="font-semibold text-gray-700"> NIK : </label>
      <input
        type="text"
        id="nik"
        class="p-3 border rounded-lg"
        v-model="inputForm.nik"
        required
      />
    </div>
    <div class="input-field flex flex-col gap-2">
      <label for="nama" class="font-semibold text-gray-700"> Nama : </label>
      <input
        type="text"
        id="nama"
        class="p-3 border rounded-lg"
        v-model="inputForm.nama"
        required
      />
    </div>
    <div class="input-field flex flex-col gap-2">
      <label for="nilai" class="font-semibold text-gray-700"> Nilai : </label>
      <input
        type="number"
        id="nilai"
        class="p-3 border rounded-lg"
        max="100"
        v-model="inputForm.nilai"
        required
      />
    </div>
    <button class="bg-blue-500 w-full p-3 rounded-lg text-white font-semibold">
      SUBMIT
    </button>
  </form>
</template>
