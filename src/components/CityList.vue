<template>
  <div v-for="city in savedCities" :key="city.id">
    <CityCard :city="city" />
  </div>
</template>

<script setup>
import axios from "axios";
import CityCard from "./CityCard.vue";
import { ref } from "vue";

// Retrieving data from LocalStorage

const savedCities = ref([]);
const getCities = async () => {
  if (localStorage.getItem("savedCities")) {
    savedCities.value = JSON.parse(localStorage.getItem("savedCities"));

    // we are iterating over savedCities array using for loop and for each city inside
    //  the array we are going to make request and push that request into "requests" array
    const requests = [];
    savedCities.value.forEach((city) => {
      requests.push(
        axios.get(
          `https://api.openweathermap.org/data/2.5/weather?lat=${city.coords.lat}&lon=${city.coords.lng}&appid=7efa332cf48aeb9d2d391a51027f1a71&units=metric`
        )
      );
    });

    const weatherData = await Promise.all(requests);

    weatherData.forEach((value, index) => {
      savedCities.value[index].weather = value.data;
    });
  }
};

await getCities();
</script>
