<template>
  <v-card>
    <v-toolbar color="cyan" dark flat>
      <v-btn icon @click="$router.go(-1)">
        <v-icon>mdi-chevron-left</v-icon>
      </v-btn>
      <v-toolbar-title>詳細</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn :href="company.url" target="_blank" color="primary">企業ページ</v-btn>
    </v-toolbar>
    <v-card-title class="headline">{{company.name}}</v-card-title>
    <v-card-text class="body-1">{{company.summary}}</v-card-text>
    <v-card-actions>
      <v-spacer></v-spacer>
      <v-btn :href="company.url" target="_blank" color="primary">会社のホームページを開く</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      companys: []
    };
  },
  props: {
    company: Object,
    id: String
  },
  methods: {
    openCompanyPage() {
      window.open(this.company.url, "google");
    }
  }
};
</script>
