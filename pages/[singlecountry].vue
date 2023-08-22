<template>
  <div>
  <p>
    country name:  {{ country.singlecountry }}
  </p>
      <ul>
        country borders:   
        <li v-for="(item, i) in resultBorder" :key="i">
          <!-- <img class="flag" :src="item.img" :alt="item.alt" /> -->
          <div>
            <span style="padding-right:2%" v-for="border in item.borders">
 {{ border }}
            </span>
          </div>
        </li>
      </ul>
  </div>
</template>

<script setup>
// const country = useRouter().params;
const country = useRoute().params;

console.log(useRoute());

const url = `https://restcountries.com/v3.1/name/${country.singlecountry}`;

const resultBorder = await $fetch(url).catch((error) => error.data);

console.log(url);
</script>

<style>
ul, li{
list-style: none;
padding: 0;
}
</style>
