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
        <p>
          検索キーワード：{{ keyword }}
        </p>
      </v-flex>
        <v-col
          v-for="(book, i) in books"
          :key="i"
          cols="12"
        >
          <v-card
            color="#777"
            dark
            :href="book.volumeInfo.infoLink"
            target="_blank"
          >
            <div class="d-flex flex-no-wrap justify-space-between">
              <div>
                <v-card-title
                  class="text-h5"
                  v-text="book.volumeInfo.title"
                ></v-card-title>
                <div v-for="(author, j) in book.volumeInfo.authors" :key="j">
                  <p class="px-4 py-1 mb-0">{{ author }}</p>
                </div>
              </div>

              <v-avatar
                class="ma-3"
                size="125"
                tile
              >
                <v-img v-if="book.volumeInfo.imageLinks !== undefined && book.volumeInfo.imageLinks.smallThumbnail !== undefined" :src="book.volumeInfo.imageLinks.smallThumbnail  "></v-img>
              </v-avatar>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
import axios from "axios"
  export default {
    props: ['keyword'],
    data() {
      return {
        books: [],
      }
    },
    async created() {
      const response = await axios.get(`https://www.googleapis.com/books/v1/volumes?maxResults=40&q=${this.keyword}`);
      this.books = response.data.items;
    } 
  }
</script>
