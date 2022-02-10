<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold my-3">
          書籍検索
        </h1>
        <v-text-field 
        label="著者名または作品名を入力してください。"
        v-model="keyword"
        required>
        </v-text-field>
        <v-btn @click="search"><span>検索</span></v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    data() {
      return {
        keyword: ''
      }
    },
    methods: {
      search() {
        this.$router.push(`/result/${this.keyword}`);
      }
    }
  }
</script>
