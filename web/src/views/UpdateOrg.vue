<template>
  <v-container class="mb-4">
    <v-row>
      <v-col>
        <h2 class="my-4 display-1">
          Update Organization
        </h2>
        <v-btn to="/manage" text
          ><v-icon>mdi-chevron-left</v-icon> Back to organizations</v-btn
        >

        <v-toolbar dense flat class="mb-3">
          <v-toolbar-title>Organization Details</v-toolbar-title>
        </v-toolbar>
        <v-row>
          <v-col md="3" sm="4">Name</v-col>
          <v-col class="record-value">{{ record.name }}</v-col>
        </v-row>
        <v-row>
          <v-col md="3" sm="4">Business Number</v-col>
          <v-col class="record-value">{{ record.sourceId }}</v-col>
        </v-row>
        <v-row>
          <v-col md="3" sm="4">Status</v-col>
          <v-col class="record-value">{{ record.status }}</v-col>
        </v-row>

        <v-toolbar dense flat class="mb-3">
          <v-toolbar-title>Services Offered</v-toolbar-title>
        </v-toolbar>

        <v-row align="center" justify="start">
          <v-col v-if="!record.services.length">
            <v-alert color="primary" class="mb-0" text icon="mdi-information"
              >No services added</v-alert
            >
          </v-col>
          <v-col
            v-for="service in record.services"
            :key="service.id"
            class="shrink"
          >
            <v-chip>
              <v-icon left v-text="service.icon"></v-icon>
              {{ service.name }}
            </v-chip>
          </v-col>
        </v-row>

        <v-toolbar dense flat class="mb-3">
          <v-toolbar-title>Registered Employees</v-toolbar-title>
          <v-spacer></v-spacer>
          <v-btn color="primary" to="/add-employee">Add Employee</v-btn>
        </v-toolbar>

        <employees-table></employees-table>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped lang="scss">
.record-value {
  font-weight: 600;
}
</style>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { Organization } from "@/models/organization";
import EmployeesTable from "./EmployeesTable.vue";

@Component({ components: { EmployeesTable } })
export default class ManageOrg extends Vue {
  private record: Organization = {
    id: "1",
    sourceId: "BC989125",
    name: "John's Cleaners",
    status: "Essential",
    services: [
      {
        id: "1",
        name: "Medical Facility Services",
        icon: "mdi-medical-bag"
      },
      {
        id: "2",
        name: "Doctor",
        icon: "mdi-doctor"
      },
      {
        id: "1",
        name: "Nurse",
        icon: "mdi-doctor"
      },
      {
        id: "1",
        name: "Cleaning",
        icon: "mdi-broom"
      },
      {
        id: "1",
        name: "Sanitation",
        icon: "mdi-trash-can-outline"
      },
      {
        id: "1",
        name: "HVAC Repair",
        icon: "mdi-water-boiler"
      },
      {
        id: "2",
        name: "IT",
        icon: "mdi-laptop"
      }
    ]
  };

  created() {
    //
  }
}
</script>
