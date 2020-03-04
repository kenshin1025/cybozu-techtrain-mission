<template>
  <v-card>
    <v-card-title class="headline">{{company.name}}</v-card-title>
    <v-card-text>{{company.summary}}</v-card-text>
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
      company: Object
  }
};
</script>