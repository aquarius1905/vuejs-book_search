<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold my-3">
          書籍検索
        </h1>
        <v-form ref="form">
          <v-text-field 
          label="著者名または作品名を入力してください。"
          v-model="keyword"
          :rules="[required]"
          >
          </v-text-field>
          <v-btn @click="search"><span>検索</span></v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    data() {
      return {
        keyword: '',
        required: value => !!value || "必ず入力してください",
      }
    },
    methods: {
      search() {
        if (this.$refs.form.validate()) {
          this.$router.push(`/result/${this.keyword}`);
        }
      }
    }
  }
</script>
