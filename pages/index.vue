<template>
  <div>
    <ul class="counteries-container">
      <li
        class="counteries-item"
        v-for="country in countries"
        :key="country.cca3"
      >
        <NuxtLink
          :to="{
            name: 'singlecountry',
            params: {
              singlecountry: country.name.common,
            //   singlecountryImage: country.flags.png,
            },
          }"
        >
          <img
            class="img-container"
            :src="country.flags.png"
            :alt="country.flags.alt"
            :title="country.name.common"
          />

          <p class="country-name">{{ country.name.common }}</p>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>



<script setup>
import { ref } from "vue";
const countries = ref([]);

const getCountries = async (query) => {
  const url = query
    ? `https://restcountries.com/v3.1/name/${query}`
    : "https://restcountries.com/v3.1/all";
  const response = await fetch(url);
  countries.value = await response.json();
};

getCountries();
</script>

<style>
.counteries-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  list-style: none;
}
.counteries-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 1px solid rgb(58, 58, 58);
  margin: 5px;
  border-radius: 10px;
  justify-content: center;
  width: 200px;
  height: 150px;
}
.counteries-item a {
  color: rgb(58, 58, 58);
  text-align: center;
  font-weight: bold;
  text-decoration: none;
  font-family: "Times New Roman";
  font-size: 14px;
}
.img-container {
  width: 180px;
  height: 85px;
  border-radius: 10px;
}
</style>
