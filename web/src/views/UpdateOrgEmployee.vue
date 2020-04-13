<template>
  <v-container class="mb-4">
    <v-row>
      <v-col>
        <h2 class="my-4 display-1">
          {{ record.name }}
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
          <v-toolbar-title>Service Delivery Credential</v-toolbar-title>
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
            ><v-btn small outlined>Issue</v-btn></template
          >
        </v-data-table>

        <v-toolbar dense flat class="mb-3">
          <v-toolbar-title>Other Credentials</v-toolbar-title>
        </v-toolbar>

        <v-data-table
          :headers="credHeaders"
          :items="credentials"
          :items-per-page="10"
          class="elevation-1"
        >
          <template v-slot:item.reason="{ value }"
            ><div v-for="reason of value" :key="reason">{{ reason }}</div>
          </template>

          <template v-slot:item.issuer="{ value }"
            ><a :href="value.href">{{ value.name }}</a>
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
  private orgName = "ABC Cleaners, Inc.";

  private orgHeaders = [
    { text: "Organization", value: "name", sortable: true, width: "40%" },
    {
      text: "Services Provided",
      value: "services",
      sortable: false,
      width: "40%"
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

  private credHeaders = [
    { text: "Credential", value: "name", sortable: true },
    { text: "Reason", value: "reason", sortable: false },
    { text: "Credential Issuer", value: "issuer", sortable: true }
  ];

  private credentials = [
    {
      id: "1",
      name: "BC Personal Health Number",
      reason: [
        "Needed in order to get a COVID-19 test.",
        "Must have a Service Provider from an essential service."
      ],
      issuer: { name: "BC Ministry of Health", href: "#" }
    },
    {
      id: "2",
      name: "COVID-19 Clear",
      reason: [
        "Needed for gaining access to some facilities.",
        "Must have a PHN Credential."
      ],
      issuer: { name: "MedLab Web", href: "#" }
    }
  ];

  created() {
    //
  }
}
</script>
