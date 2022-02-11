<template>
  <v-card
    color="#777"
    dark
    :href="book.volumeInfo.infoLink"
    target="_blank"
    class="mb-3"
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
        <v-img v-if="book.volumeInfo.imageLinks !== undefined && book.volumeInfo.imageLinks.smallThumbnail !== undefined" :src="book.volumeInfo.imageLinks.smallThumbnail"></v-img>
        <v-img v-else src="../assets/book.png"></v-img>
      </v-avatar>
    </div>
  </v-card>
</template>

<script>
export default {
  props: {
    keyword: String,
    book: Object
  }
}
</script>
