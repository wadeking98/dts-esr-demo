<template>
  <v-container class="mb-4">
    <v-row>
      <v-col>
        <h2 class="my-4 display-1">
          Add / Update Employee
        </h2>
        <v-btn to="/update" text
          ><v-icon>mdi-chevron-left</v-icon> Back to {{ orgName }}</v-btn
        >
        <v-skeleton-loader
          boilerplate
          type="paragraph"
          class="mt-2"
        ></v-skeleton-loader>
        <br />

        <v-toolbar dense flat class="mb-3">
          <v-toolbar-title>Employee Details</v-toolbar-title>
        </v-toolbar>
        <v-row>
          <v-col md="3" sm="4" class="pt-6">Name</v-col>
          <v-col class="record-value"
            ><v-text-field
              outlined
              hide-details
              v-model="record.name"
            ></v-text-field
          ></v-col>
        </v-row>
        <v-row>
          <v-col md="3" sm="4" class="pt-6">Email Address</v-col>
          <v-col class="record-value"
            ><v-text-field
              outlined
              hide-details
              type="email"
              v-model="record.email"
            ></v-text-field
          ></v-col>
        </v-row>
        <v-row>
          <v-col md="3" sm="4" class="pt-6">Services Offered</v-col>
          <v-col class="record-value"
            ><template v-for="svc of serviceOptions"
              ><v-switch
                :label="svc.name"
                dense
                :key="svc.id"
                v-model="serviceSel"
                :value="svc.id"
              ></v-switch></template
          ></v-col>
        </v-row>
      </v-col>
    </v-row>
    <div style="text-align: right">
      <v-btn to="/update" color="primary" outlined class="mr-2">Cancel</v-btn>
      <v-btn to="/employee-email" color="primary">Send Invitation</v-btn>
    </div>
  </v-container>
</template>

<style scoped lang="scss"></style>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { Service } from "@/models/organization";

@Component
export default class ManageOrg extends Vue {
  private record = {
    id: "1",
    name: "Michelle Sanches",
    email: "michelle.sanches@abccleaners.ca"
  };
  private orgName = "John's Cleaners";

  private serviceSel = ["1", "2"];

  private serviceOptions: Service[] = [
    {
      id: "1",
      name: "Medical Facility Services",
      icon: "mdi-medical-bag"
    },
    {
      id: "2",
      name: "Cleaning",
      icon: "mdi-broom"
    }
  ];

  created() {
    //
  }
}
</script>
