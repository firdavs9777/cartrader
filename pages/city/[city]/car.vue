<script setup>
// Router name
const route = useRoute();
const {toTitleCase} = useUtilities()
useHead({
  title: `${
    route.params.make ? toTitleCase(route.params.make) : 'Cars'
  } in ${toTitleCase(route.params.city)}`
});
// using custom layout in car page
definePageMeta({
  layout: 'custom'
});

</script>
<template>
  <div>
    <!-- CARS PAGE -->
    <div class="mt-32 flex">
      <!-- CAR SIDE BAR -->
      <CarSideBar />
      <!-- CAR CARDS -->
      <NuxtPage />
    </div>
  </div>
</template>
