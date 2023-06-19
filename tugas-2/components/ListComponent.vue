<script>
export default {
  props: {
    dataSiswa: {
      type: Array,
    },
  },
  computed: {
    nilaiAverage() {
      const arrayNilai = this.dataSiswa.map((siswa) => siswa.nilai)
      const sumNilai = arrayNilai.reduce(
        (total, value) => total + Number(value)
      )
      return sumNilai / arrayNilai.length
    },
  },
}
</script>

<template>
  <table class="text-center border mt-5">
    <thead>
      <tr class="border bg-slate-300">
        <th>No.</th>
        <th>NIK</th>
        <th>Nama</th>
        <th>Nilai</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(siswa, index) in dataSiswa" :key="siswa.nik">
        <td>{{ index + 1 }}</td>
        <td>{{ siswa.nik }}</td>
        <td>{{ siswa.nama }}</td>
        <td>{{ siswa.nilai }}</td>
      </tr>
    </tbody>
    <tfoot>
      <tr class="bg-blue-200">
        <td colspan="3">Nilai rata-rata :</td>
        <td>{{ nilaiAverage }}</td>
      </tr>
    </tfoot>
  </table>
</template>
