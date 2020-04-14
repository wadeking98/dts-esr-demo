<template>
  <v-container class="mb-4">
    <v-row>
      <v-col>
        <h1 class="my-4 display-1">
          Registering your Business as an Essential Service
        </h1>
        <v-skeleton-loader boilerplate type="paragraph"></v-skeleton-loader>
        <br />
        <v-skeleton-loader boilerplate type="sentences"></v-skeleton-loader>
        <br />
        <v-expansion-panels>
          <v-expansion-panel>
            <div class="num-row">
              <div class="number">1</div>
              <div class="num-body">
                <v-expansion-panel-header
                  ><h3>Get a Digital Wallet</h3></v-expansion-panel-header
                >
                <v-expansion-panel-content>
                  <v-skeleton-loader
                    boilerplate
                    type="sentences"
                  ></v-skeleton-loader>
                  <v-btn href="https://github.com/bcgov/identity-kit-poc/blob/master/docs/GettingApp.md" target="_blank" color="primary" class="my-2"
                    >Instructions</v-btn
                  >
                </v-expansion-panel-content>
              </div>
            </div>
          </v-expansion-panel>
          <v-expansion-panel>
            <div class="num-row">
              <div class="number">2</div>
              <div class="num-body">
                <v-expansion-panel-header
                  ><h3>
                    Get the Mobile Services App and Card
                  </h3></v-expansion-panel-header
                >
                <v-expansion-panel-content>
                  <v-skeleton-loader
                    boilerplate
                    type="paragraph"
                  ></v-skeleton-loader>
                  <p>Although for this demo, you should <b>skip this step</b>, the link to the instructions is live and can be used.</p>
                  <v-btn href="https://www2.gov.bc.ca/gov/content/governments/government-id/bc-services-card/login-with-card/mobile-card/download-bcsc-app" target="_blank" color="primary" class="my-2"
                    >Instructions</v-btn
                  >
                </v-expansion-panel-content>
              </div>
            </div>
          </v-expansion-panel>
          <v-expansion-panel>
            <div class="num-row">
              <div class="number">3</div>
              <div class="num-body">
                <v-expansion-panel-header
                  ><h3>
                    Get the Verified Person Credential using your Mobile
                    Services Card
                  </h3></v-expansion-panel-header
                >
                <v-expansion-panel-content>
                  <v-skeleton-loader
                    boilerplate
                    type="sentences"
                  ></v-skeleton-loader>
                  <p>For this demo get the <b>Unverified Person</b>. The "Verified Person" link is a limited access service requiring you have both an invitation to the program and an activated BC Gov Services Card App</p>
                  <v-btn href="https://openvp-issuer-dev.pathfinder.gov.bc.ca/" target="_blank" color="primary" class="my-2"
                    >Unverified Person</v-btn
                  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<v-btn href="https://identity-kit.pathfinder.gov.bc.ca/" target="_blank" color="tertiary" class="my-2"
                    >Verified Person</v-btn
                  >
                </v-expansion-panel-content>
              </div>
            </div>
          </v-expansion-panel>
          <v-expansion-panel>
            <div class="num-row">
              <div class="number">4</div>
              <div class="num-body">
                <v-expansion-panel-header
                  ><h3>
                    Register your Company/Organization as an BC Essential
                    Service
                  </h3></v-expansion-panel-header
                >
                <v-expansion-panel-content>
                  <v-skeleton-loader
                    boilerplate
                    type="paragraph"
                  ></v-skeleton-loader>
                  <v-btn to="/manage" color="primary" class="my-2"
                    >Register your Organization</v-btn
                  >
                </v-expansion-panel-content>
              </div>
            </div>
          </v-expansion-panel>
        </v-expansion-panels>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped lang="scss">
.num-row {
  display: flex;
  .number {
    position: relative;
    font-size: 1.5rem;
    padding-right: 0.6em;
    padding-top: 0.25em;
    text-align: right;
    width: 2em;
    &::after {
      display: block;
      background: var(--v-accent-darken3);
      border-radius: 6px;
      content: "";
      position: absolute;
      top: 0.2em;
      bottom: 0.2em;
      right: 0;
      width: 3px;
    }
  }
  .num-body {
    flex: auto;
  }
}
</style>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class Home extends Vue {}
</script>
