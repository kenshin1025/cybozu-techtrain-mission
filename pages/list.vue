<template>
  <v-layout justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-container fluid>
        <v-row dense>
          <v-col cols="12" v-for="(company, i) in companys" :key="i">
            <ListCell :company="company" :id="companyIds[i]"/>
          </v-col>
        </v-row>
      </v-container>
    </v-flex>
  </v-layout>
</template>

<script>
import ListCell from "@/components/ListCell";
import firebase from "@/plugins/firebase";

export default {
  components: {
    ListCell
  },
  data() {
    return {
      companyIds: [],
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
          this.companyIds == [];
          this.companys == [];
          snapshot.forEach(doc => {
            this.companyIds.push(doc.id);
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
