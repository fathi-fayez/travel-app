<!-- eslint-disable -->
<template>
  <div id="nav">
    <AppLink id="logo" to="/">Vue School Travel App</AppLink>
    <div class="destination-links">
      <AppLink
        v-for="destination in destinations"
        :key="destination.id"
        :to="{
          name: 'destination.show',
          params: { id: destination.id, slug: destination.slug },
        }"
      >
        {{ destination.name }}
      </AppLink>
      <AppLink :to="{ name: 'protected' }">Dashboard</AppLink>
    </div>
  </div>
</template>
<!-- eslint-disable -->
<script>
import sourceData from "@/data.json";
import AppLink from "./AppLink.vue";

export default {
  components: { AppLink },
  data() {
    return {
      destinations: sourceData.destinations,
    };
  },
};
</script>
