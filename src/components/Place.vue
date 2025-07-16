<script setup>
import LocationCarrousel from './LocationCarrousel.vue';

const props = defineProps({
  t: Object
})

</script>

<template>
  <section id="location" class="text-center bg-base-300 w-full flex flex-col lg:flex-row-reverse justify-center items-center gap-5 h-fit p-5 pb-15 pt-20 px-5 md:px-10">
    <div class="w-full md:w-2/3 text-xl">
      <h2 class="text-5xl text-secondary-content font-extrabold font-title pb-2">{{ $props.t.locationTitle }}</h2>
      <div class="flex flex-col gap-5" v-html="$props.t.locationInfo"></div>
    </div>
    <div class="w-full md:w-1/3">
      <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3149.4087292507666!2d-4.857918923540835!3d37.874123071960646!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd6d27816af6147b%3A0xdd5872b23f40d3e!2sHuerta%2028!5e0!3m2!1ses!2ses!4v1752596432449!5m2!1ses!2ses" class="w-full md:h-96 rounded-xl" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
    </div>
  </section>
  <LocationCarrousel />
</template>