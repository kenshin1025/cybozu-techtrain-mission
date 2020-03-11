<template>
  <!-- <v-card :href="company.url" target="_blank"> -->
  <v-card nuxt :to="'company/'+id">
    <v-card-title class="headline text-truncate">{{company.name}}</v-card-title>
    <v-card-text class="text-truncate">{{company.summary}}</v-card-text>
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