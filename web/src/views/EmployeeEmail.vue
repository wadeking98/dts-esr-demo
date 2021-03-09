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
              <span class="fld">Invitation to get your Essential Service Provider credentials</span>
            </p>
            <v-divider class="my-4" />
            <p>Michelle,</p>
            <p> This email contains your invitation to be issued digital credentials about your work as an essential services provider in BC.</P>
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
              <span class="fld">Medical Facility Services, Cleaning</span>
            </p>
            <p>
              <span class="hdr2">Requesting Person:</span>
              <span class="fld">Mary Robinson</span>
            </p>
            <br />
            <p>Please complete these steps to get what you need to receive and use your essential worker credentials:</p>
            <ul>
              <li>Follow these <a href="https://github.com/bcgov/identity-kit-poc/blob/master/docs/GettingApp.md"
                  target="_blank">instructions</a> to get a digital wallet to hold and use your credentials.
              </li>
              <li>
                &nbsp;&nbsp;&nbsp;Get your BC 
                <a href="https://openvp-issuer.apps.silver.devops.gov.bc.ca/"
                      target="_blank">(un)Verified Person</a> Credential.
              </li>
              <li>
                &nbsp;&nbsp;&nbsp;Get your BC Essential Services Provider Credentials by
                <router-link to="/employee">accepting this Invitation</router-link>.
              </li>
            </ul>
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
