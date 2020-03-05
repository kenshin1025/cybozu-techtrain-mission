<template>
  <!-- <v-card :href="company.url" target="_blank"> -->
  <v-card>
    <v-card-title class="headline">
      <a :href="company.url" target="_blank" class="text-truncate">{{company.name}}</a>
    </v-card-title>
    <v-card-text class="text-truncate">{{company.summary}}</v-card-text>
  </v-card>
</template>

<style scoped>
a {
  color: black;
}
</style>

<script>
export default {
  data() {
    return {
      companys: []
    };
  },
  props: {
    company: Object
  },
  methods: {
    openCompanyPage() {
      window.open(this.company.url, "google");
    }
  }
};
</script>