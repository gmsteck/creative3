<template>
  <div class="wrapper">
    <div class="products">
      <div class="product" v-for="park in parks" :key="park.Name">
        <div class="info">
          <h1>{{ park.Name }}</h1>
          <p>{{park.State}}</p>
          <p>{{park.Size}} acres</p>
        </div>
        <div class="image">
          <img :src="'/images/' + park.Image" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ParkList",
  props: {
    parks: Array,
  },
};
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.product {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
}

.product img {
  border: 2px solid #333;
  height: 250px;
  width: 200px;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #f2921d;
  color: #000;
  padding: 10px 30px;
  height: 80px;
}

.info h1 {
  font-size: 16px;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}

.price {
  display: flex;
}

button {
  height: 50px;
  background: rgb(48, 48, 48);
  color: white;
  border: none;
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
