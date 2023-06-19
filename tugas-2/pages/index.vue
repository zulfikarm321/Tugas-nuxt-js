<script>
import ListComponent from '@/components/ListComponent.vue'
import FormComponent from '@/components/FormComponent.vue'

export default {
  components: { ListComponent, FormComponent },
  data() {
    return {
      data: [
        {
          nik: '01234',
          nama: 'Zulfikar Muhamad',
          nilai: 90,
        },
      ],
    }
  },
  methods: {
    addData(data) {
      const existingNik = this.data.find((value) => value.nik === data.nik)

      if (existingNik) {
        alert('Nik sudah ada')
        return
      }

      this.data.push(data)
    },
  },
}
</script>

<template>
  <div class="container mx-auto flex flex-col gap-5 max-w-xl py-5">
    <FormComponent @onSubmit="addData" />
    <ListComponent :dataSiswa="data" />
  </div>
</template>
