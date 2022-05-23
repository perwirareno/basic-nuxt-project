<template>
  <b-container fluid="md" class="mt-5 mb-5">
    <b-row>
      <b-col md="12">
        <b-card class="shadow-md border-0 rounded-lg">
          <h5>DATA POSTS</h5>
          <hr />
          <b-button pill variant="danger" class="mb-3" @click="goToPrev()"
            >Kembali</b-button
          >
          <b-button
            :to="{ name: 'post-create' }"
            pill
            variant="primary"
            class="mb-3"
            >Tambah Area</b-button
          >
          <!-- <b-table striped bordered hover :items="items" :fields="fields" show-empty></b-table> -->
          <b-table
            striped
            bordered
            hover
            :items="posts"
            :fields="fields"
            show-empty
          ></b-table>
        </b-card>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  data() {
    return {
      //header table
      fields: ['title', 'content', 'actions'],
      //posts data
      posts: [],
    }
  },

  methods: {
    goToPrev() {
      this.$router.go(-1)
    }
  },

  mounted() {
    //fething ke Rest API
    this.$axios
      .get('/api/posts')
      .then((response) => {
        //assign response ke state "posts"
        this.posts = response.data.data
      })
      .catch((error) => {
        console.log(error.response.data)
      })
  },
}
</script>

<style>
</style>