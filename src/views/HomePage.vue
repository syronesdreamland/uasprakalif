<template>
  <div class="homepage">
    <Weather />
  </div>
</template>

<script>
import Weather from '../components/WeatherWidget.vue';

  export default {
    name: 'HomePage',
    components: {
      Weather,
    }
  };
</script>

<style>
.homepage {
  text-align: center;
}
</style>
