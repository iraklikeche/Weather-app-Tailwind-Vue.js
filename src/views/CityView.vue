<template>
  <div>
    <Suspense>
      <AsynCityView />
      <template #fallback>
        <p>Loading...</p>
      </template>
    </Suspense>
  </div>
</template>

<script setup>
import AsynCityView from "../components/AsynCityView.vue";
</script>
