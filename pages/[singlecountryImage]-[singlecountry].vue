<template>
  <div>
    {{ country.singlecountry }}
    <img :src="country.singlecountryImage" />

  </div>
</template>

<script setup>
// const country = useRouter().params;
const country = useRoute().params;

console.log(useRoute());
</script>

<style>

</style>
