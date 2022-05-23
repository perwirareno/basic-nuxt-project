<template>
  <div>
    <b-button pill class="mb-3" variant="danger" @click="goToPrev()"
      >Kembali</b-button
    >
    <b-button id="my-modal" pill class="mb-3" variant="primary" @click="showModal"
      >Tambah Area</b-button
    >

    <b-button to="/post" pill class="mb-3" variant="success"
      >Tambah Area Page</b-button
    >

    <!-- Modal -->
    <b-form @submit="store">
      <b-modal ref="my-modal" hide-footer title="Tambah Master Area">
        <b-row class="my-0">
          <b-col sm="3">
            <label for="input-kode-area">Kode Area</label>
          </b-col>
          <b-col sm="9">
            <b-form-input
              id="input-kode-area"
              type="text"
              v-model="post.title"
              :class="{ 'is-invalid': validation.title }"
              placeholder="Masukkan kode area..."
            ></b-form-input>
            <div v-if="validation.title" class="mt-2">
              <b-alert show variant="danger">{{ validation.title[0] }}</b-alert>
            </div>
          </b-col>
        </b-row>

        <b-row class="my-3">
          <b-col sm="3">
            <label for="input-nama-area">Nama Area</label>
          </b-col>
          <b-col sm="9">
            <b-form-input
              id="input-nama-area"
              v-model="post.content"
              :class="{ 'is-invalid': validation.title }"
              placeholder="Masukkan nama area..."
            ></b-form-input>
            <div v-if="validation.content" class="mt-2">
              <b-alert show variant="danger">{{
                validation.content[0]
              }}</b-alert>
            </div>
          </b-col>
        </b-row>

        <!-- Button -->
        <div class="col-mt-12 text-right">
          <b-button
            pill
            class="mt-2"
            variant="outline-danger"
            @click="hideModal"
            >Tutup</b-button
          >
          <b-button type="submit" pill class="mt-2" variant="outline-success"
            >Simpan</b-button
          >
        </div>
      </b-modal>
    </b-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      //state post
      post: {
        title: '',
        content: '',
      },
      //state validation
      validation: [],
    }
  },
  methods: {
    showModal() {
      this.$refs['my-modal'].show()
    },
    hideModal() {
      this.$refs['my-modal'].hide()
    },

    goToPrev() {
      this.$router.go(-1);
    },

    //method "store"
    async store(e) {
      e.preventDefault()
      console.log(e)

      //send data ke Rest API
      await this.$axios
        .post('/api/posts', {
          //data yang dikirim ke server
          title: this.post.title,
          content: this.post.content,
        })
        .then(() => {
          //redirect ke route "post"
          this.$router.push({
            name: 'post',
          })
        })
        .catch((error) => {
          //assign validation
          this.validation = error.response.data
        })
    },
  },
}
</script>