<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-container>
        <v-row dense>
          <v-col cols="12" v-for="(company, i) in companys" :key="i">
            <ListCell :company="company" />
          </v-col>
        </v-row>
      </v-container>
    </v-flex>
  </v-layout>
</template>

<script>
import ListCell from "@/components/ListCell";
import firebase from "../plugins/firebase";

export default {
  components: {
    ListCell
  },
  data() {
    return {
      companys: []
    };
  },
  methods: {
    test() {
      firebase
        .firestore()
        .collection("companys")
        .get()
        .then(snapshot => {
          this.companys == [];
          snapshot.forEach(doc => {
            this.companys.push(doc.data());
          });
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