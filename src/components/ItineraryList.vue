<template>
  <div>
    <div class="list">
      <div class="park" v-for="park in parks" :key="park.Name">
        <div>
          <div class="image">
            <img :src="'/images/' + park.Image" />
          </div>
          <h1>{{ park.Name }}</h1>
          <p>{{ park.State }}</p>
          <p>{{ park.Size }} acres</p>
        </div>
        <div class="add">
          <button class="auto" @click="remove(park)">
            Remove from Itinerary
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ItineraryList",
  props: {
    parks: Array,
  },
  methods: {
    remove(park) {
      this.$root.$data.parkList.splice(park, 1);
    },
    distance(lat1, lat2, lon1, lon2) {
      // The math module contains a function
      // named toRadians which converts from
      // degrees to radians.
      lon1 = (lon1 * Math.PI) / 180;
      lon2 = (lon2 * Math.PI) / 180;
      lat1 = (lat1 * Math.PI) / 180;
      lat2 = (lat2 * Math.PI) / 180;

      // Haversine formula
      let dlon = lon2 - lon1;
      let dlat = lat2 - lat1;
      let a =
        Math.pow(Math.sin(dlat / 2), 2) +
        Math.cos(lat1) * Math.cos(lat2) * Math.pow(Math.sin(dlon / 2), 2);

      let c = 2 * Math.asin(Math.sqrt(a));

      // Radius of earth in kilometers. Use 3956
      // for miles
      let r = 6371;

      // calculate the result
      return c * r;
    },
  },
};
</script>

<style scoped>
.image {
  display: inline-block;
  position: relative;
  width: 200px;
  height: 200px;
  overflow: hidden;
  border-radius: 50%;
}

img {
  width: auto;
  height: 100%;
  margin-left: -50px;
}

.list {
  display: inline-flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-content: space-around;
  justify-content: center;
  border-radius: 10px;
  margin-bottom: 60px;
  margin-top: 60px;
}

.park {
  margin: 20px;
}

button {
  height: 50px;
  background: rgb(68, 68, 68);
  color: white;
  border: none;
  border-radius: 5%;
}

button:hover {
  height: 50px;
  background: rgb(48, 48, 48);
  color: white;
  border: none;
  border-radius: 5%;
}

button:active {
  height: 50px;
  background: #000;
  color: white;
  border: none;
  -webkit-box-shadow: inset 0px 0px 5px #c1c1c1;
  -moz-box-shadow: inset 0px 0px 5px #c1c1c1;
  box-shadow: inset 0px 0px 5px #c1c1c1;
}

.auto {
  margin-left: auto;
}
</style>
