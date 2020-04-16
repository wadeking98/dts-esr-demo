<template>
  <v-container class="mb-4">
    <v-row>
      <v-col>
        <h2 class="my-4 display-1">
          Emailed Invitation
        </h2>
        <v-btn to="/update" text
          ><v-icon>mdi-chevron-left</v-icon> Back to {{ orgName }}</v-btn
        >

        <v-card class="mt-3" outlined>
          <v-card-text class="body-1">
            <p>
              <span class="hdr">To:</span>
              <span class="fld">michelle.sanches@abccleaners.ca</span>
            </p>
            <p>
              <span class="hdr">From:</span>
              <span class="fld">noreply@esr.gov.bc.ca</span>
            </p>
            <p>
              <span class="hdr">Subject:</span>
              <span class="fld">Register as an Essential Service Provider</span>
            </p>
            <v-divider class="my-4" />
            <p>Michelle,</p>
            <p> This email contains your invitation to be issued verified credentials about your work as an essential services worker in BC.</P>
            <v-skeleton-loader boilerplate />
              <v-skeleton-loader
                boilerplate
                type="paragraph"
              ></v-skeleton-loader>
            <p></p>
            <p>
              <span class="hdr2">Requesting Employer:</span>
              <span class="fld">ABC Cleaning, Inc.</span>
            </p>
            <p>
              <span class="hdr2">Services Provided:</span>
              <span class="fld">Medical Facility Cleaning Service</span>
            </p>
            <p>
              <span class="hdr2">Requesting Person:</span>
              <span class="fld">Mary Robinson</span>
            </p>
            <br />
            <p>Please follow these instructions to get all of the elements you need to get your essential worker credentials:</p>
            <p>Get a digital wallet:&nbsp; <a href="https://github.com/bcgov/identity-kit-poc/blob/master/docs/GettingApp.md"
                    target="_blank">Instructions</a></p>
            <v-alert text border="left" color="secondary darken-1" icon="mdi-flag">
              Skip this step as it is not needed for this demo.
            <p>
              <br>
              Get your BC Services Card App and digital BC Services Card:&nbsp; <a href="https://www2.gov.bc.ca/gov/content/governments/government-id/bc-services-card/login-with-card/mobile-card/download-bcsc-app"
                    target="_blank">Instructions</a>
            </p>
            </v-alert>
            <p>
              Get your BC Un-Verified Person Credential:&nbsp;
              <a href="https://openvp-issuer.pathfinder.gov.bc.ca/"
                    target="_blank">Instructions</a>
            </p>
            <p>
              Get your BC Essential Services Provider Credential:&nbsp;
              <router-link to="/employee"><b>Link to Register</b></router-link>
            </p>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped lang="scss">
.hdr,
.hdr2 {
  color: #666;
  display: inline-block;
  font-size: 95%;
}
.hdr {
  min-width: 6em;
}
.hdr2 {
  min-width: 14em;
}
.fld {
  font-weight: bolder;
}
</style>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class ManageOrg extends Vue {
  private orgName = "ABC Cleaners, Inc.";
  created() {
    //
  }
}
</script>
