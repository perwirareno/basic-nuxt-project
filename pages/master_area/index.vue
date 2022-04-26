<template>
  <b-container fluid="md" class="mt-5 mb-5">
    <b-row>
      <b-col md="12">
        <b-card class="shadow-md border-0 rounded-lg">
          <h5>Master Area</h5>
          <hr />

          <!-- Modal -->
          <AddMasterArea />

          <b-table
            striped
            bordered
            hover
            :items="items_name"
            :fields="fields_name"
            show-empty
          ></b-table>
        </b-card>
      </b-col>
    </b-row>
  </b-container>
</template>

<style>
header,
h2 {
  margin-bottom: 20px;
}
.modal-area {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>

<script>
export default {
  components: {},
  data() {
    return {
      //header table
      items_name: [],
      fields_name: ['kode area', 'nama area', 'actions'],
      //posts data
      posts: [],
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