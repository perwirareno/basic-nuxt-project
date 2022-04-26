<template>
  <div>
    <b-button id="my-modal" class="mb-3" variant="primary" @click="showModal"
      >TAMBAH</b-button
    >

    <!-- Modal -->
    <b-modal ref="my-modal" hide-footer title="Tambah Master Area">
      <b-row class="my-0">
        <b-col sm="3">
          <label for="input-kode-area">Kode Area</label>
        </b-col>
        <b-col sm="9">
          <b-form-input
            id="input-kode-area"
            placeholder="Masukkan kode area..."
          ></b-form-input>
        </b-col>
      </b-row>

      <b-row class="my-3">
        <b-col sm="3">
          <label for="input-nama-area">Nama Area</label>
        </b-col>
        <b-col sm="9">
          <b-form-input
            id="input-nama-area"
            placeholder="Masukkan nama area..."
          ></b-form-input>
        </b-col>
      </b-row>

      <!-- Button -->
      <div class="col-mt-12 text-right">
        <b-button pill class="mt-2" variant="outline-danger" @click="hideModal"
          >Tutup</b-button
        >
        <b-button pill class="mt-2" variant="outline-success"
          >Simpan</b-button
        >
      </div>
    </b-modal>
  </div>
</template>

<script>
export default {
  methods: {
    showModal() {
      this.$refs['my-modal'].show()
    },
    hideModal() {
      this.$refs['my-modal'].hide()
    },
  },
}
</script>