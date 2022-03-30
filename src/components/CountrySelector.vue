<template>
  <select
    v-model="selectedCountry"
    class="form-select mt-10 block w-full border p-3 rounded"
    @change="onChange()"
  >
    <option value="0">Select Country</option>
    <option v-for="country in countries" :value="country.ID" :key="country.ID">
      {{ country.Country }}
    </option>
  </select>
</template>

<script>
export default {
  name: "CountrySelector",
  props: {
    countries: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      selectedCountry: 0,
    };
  },
  methods: {
    onChange() {
      const country = this.countries.find(
        (item) => item.ID === this.selectedCountry
      );
      console.log(country);
      this.$emit("get-country", country);
    },
  },
};
</script>

<style></style>
