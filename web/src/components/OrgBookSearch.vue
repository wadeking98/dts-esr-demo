<style lang="scss"></style>

<template>
  <v-autocomplete
    label="Orgbook Search"
    placeholder="Start typing to Search"
    prepend-icon="mdi-office-building"
    return-object
    outlined
    hide-details
    v-model="model"
    :rules="rules"
    :items="items"
    :loading="isLoading"
    :search-input.sync="searchInput"
    v-on:change="change"
    clearable
    hide-no-data
    hide-selected
    append-icon
  ></v-autocomplete>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from "vue-property-decorator";
import { Configuration } from "../models/appConfig";

@Component({})
export default class OrgBookSearch extends Vue {
  @Prop() fieldModel!: string;
  @Prop() fieldRules!: Function[];

  private appConfig!: Configuration;
  private isLoading = false;
  private entries = [];
  private searchInput = "";
  private model!: string;
  private rules!: Function[];

  created() {
    this.appConfig = this.$store.getters[
      "configuration/getConfiguration"
    ] as Configuration;

    this.model = this.fieldModel;
    this.rules = this.fieldRules;
  }

  get items() {
    return this.entries.map((entry: any) => {
      // there will only ever be 1 result in the names array
      return Object.assign({
        text: entry.names[0].text,
        value: entry.names[0].text
      });
    });
  }

  change(value: any) {
    this.$emit(
      "update:field-model",
      // For this use, want to emit just the text
      typeof value === "object" && value !== null ? value.text : value
    );
  }

  @Watch("searchInput")
  onSearchInputChanged(val: string) {
    // Minimum search length is 1 character
    if (!val || val.length < 1) return;

    // A search has already been started
    if (this.isLoading) return;

    this.isLoading = true;

    const orgbookEndpoint = this.appConfig.app.orgBook.endpoint;

    // Lazily load results
    fetch(`${orgbookEndpoint}/search/autocomplete?q=${encodeURIComponent(val)}`)
      .then(res => res.json())
      .then((res: any) => {
        this.entries = res.results;
      })
      .catch(err => {
        console.log(err);
      })
      .finally(() => (this.isLoading = false));
  }
}
</script>
