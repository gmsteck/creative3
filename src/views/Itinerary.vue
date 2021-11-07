<template>
  <div>
    <p class="none" v-if="this.$root.$data.parkList.length === 0">
      No Parks in Itinerary
    </p>
    <ItineraryList :parks="parks" />
  </div>
</template>

<script>
import ItineraryList from "../components/ItineraryList.vue";
export default {
  name: "",
  components: {
    ItineraryList,
  },
  data() {
    return {
      country: "",
    };
  },
  computed: {
    parks() {
      return this.$root.$data.parkList;
    },
  },
};
</script>

<style>
.none {
  text-align: center;
  font-size: 32px;
}
</style>
