<template>
  <v-layout justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-container fluid>
        <v-row>
          <v-col cols="12">
            <DetailCard :company="company"></DetailCard>
          </v-col>
        </v-row>
      </v-container>
    </v-flex>
  </v-layout>
</template>

<script>
import DetailCard from "@/components/DetailCard";
import firebase from "@/plugins/firebase";

export default {
  components: {
    DetailCard
  },
  data() {
    return {
      company: {}
    };
  },
  methods: {
    test() {
      firebase
        .firestore()
        .collection("companys")
        .doc(this.$route.params.id)
        .get()
        .then(doc => {
          this.company = doc.data();
        })
        .catch(err => {
          console.log("Error getting documents", err);
        });
    }
  },
  created() {
    this.test();
  }
};
</script>