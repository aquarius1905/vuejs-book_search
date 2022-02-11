<template>
  <v-card
    max-width="60%"
    class="mx-auto"
  >
    <v-container>
      <v-row dense>
      <v-flex mb-4 text-center>
        <h1 class="display-2 font-weight-bold my-3">
          検索結果
        </h1>
        <p>検索キーワード：{{ keyword }}</p>
      </v-flex>
      <v-col cols="12">
        <Card v-for="(book, i) in books" :key="i" :book="book"/>
      </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
import Card from "../components/Card";
import axios from "axios"
export default {
  props: ['keyword'],
  data() {
    return {
      books: [],
    }
  },
  components: {
    Card
  },
  async created() {
    try {
      const response = await axios.get(`https://www.googleapis.com/books/v1/volumes?maxResults=40&q=${this.keyword}`);
      this.books = response.data.items;
    } catch(error) {
      console.log(error);
    }
  },
}
</script>
