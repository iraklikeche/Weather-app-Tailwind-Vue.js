<template>
  <div>
    <Suspense>
      <AsynCityView />
      <template #fallback>
        <CityViewSkeleton />
      </template>
    </Suspense>
  </div>
</template>

<script setup>
import AsynCityView from "../components/AsynCityView.vue";
import CityViewSkeleton from "../components/CityViewSkeleton.vue";
</script>
