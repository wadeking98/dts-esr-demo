<template>
  <v-container class="mb-4">
    <v-row>
      <v-col>
        <h2 class="my-4 display-1">
          {{ record.name }}
        </h2>
        <v-skeleton-loader
          boilerplate
          type="paragraph"
          class="mt-2"
        ></v-skeleton-loader>
        <br />

        <v-toolbar dense flat class="mb-3">
          <v-toolbar-title>Organizations</v-toolbar-title>
        </v-toolbar>

        <v-data-table
          :headers="orgHeaders"
          :items="organizations"
          :items-per-page="10"
          class="elevation-1"
        >
          <template v-slot:item.services="{ value }"
            ><div v-for="(svc, idx) of value" :key="idx">
              {{ svc }}
            </div></template
          >
          <template v-slot:item.actions="{}"
            ><v-btn small outlined>Get Credential</v-btn></template
          >
        </v-data-table>

        <v-toolbar dense flat class="my-3">
          <v-toolbar-title>Safe Entry Access Authorizations</v-toolbar-title>
          <v-spacer></v-spacer>
          <v-btn color="primary">Add</v-btn>
        </v-toolbar>

        <v-data-table
          :headers="authHeaders"
          :items="authorizations"
          :items-per-page="10"
          class="elevation-1"
        >
          <template v-slot:item.services="{ value }"
            ><div v-for="(svc, idx) of value" :key="idx">
              {{ svc }}
            </div></template
          >
          <template v-slot:item.actions="{ value }"
            ><v-btn
              small
              outlined
              class="mr-2"
              v-for="act of value"
              :key="act"
              >{{ act }}</v-btn
            >
          </template>
        </v-data-table>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped lang="scss"></style>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class ManageOrg extends Vue {
  private record = {
    name: "Michelle Sanches"
  };

  private orgHeaders = [
    { text: "Organization", value: "name", sortable: true, width: "40%" },
    {
      text: "Services Provided",
      value: "services",
      sortable: false,
      width: "30%"
    },
    { text: "Actions", value: "actions", sortable: false }
  ];

  private organizations = [
    {
      id: "1",
      name: "ABC Cleaners, Inc.",
      services: ["Medical Facility", "Cleaning"],
      actions: ["issue"]
    }
  ];

  private authHeaders = [
    { text: "Facility", value: "facility", sortable: true },
    { text: "Reason", value: "services", sortable: false },
    { text: "Issue Date", value: "issued", sortable: true },
    { text: "Expiry Date", value: "expiry", sortable: true },
    { text: "Actions", value: "actions", sortable: false }
  ];

  private authorizations = [
    {
      id: "1",
      facility: "Johnson Street Extended Care",
      services: ["Medical Facility", "Cleaning"],
      issued: "2020-04-15",
      expiry: "2020-06-14",
      actions: ["Revoke", "Reissue"]
    },
    {
      id: "2",
      facility: "The Kensington",
      services: ["Medical Facility", "Cleaning"],
      issued: "2020-05-08",
      expiry: "2020-07-07",
      actions: ["Revoke", "Reissue"]
    },
    {
      id: "3",
      facility: "Robertson Manor",
      services: ["Medical Facility", "Cleaning"],
      issued: "2020-04-21",
      actions: ["Revoke", "Reissue"]
    },
    {
      id: "4",
      facility: "Victoria Villa",
      services: ["Medical Facility", "Cleaning"],
      actions: ["Issue"]
    }
  ];

  created() {
    //
  }
}
</script>
