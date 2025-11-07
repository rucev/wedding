<script setup>
import { computed, ref } from 'vue'
import LocationCarrousel from './LocationCarrousel.vue'

const props = defineProps({
  t: Object
})

const selected = ref('wedRadio')

const mapUrls = {
  prewedRadio: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d37737.97427713536!2d-4.803120348835557!3d37.898076443077564!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd6cdf284407b957%3A0xaa2cd68b347f9974!2sKon-Q%20Club!5e0!3m2!1ses!2ses!4v1762524588648!5m2!1ses!2ses', 
  busRadio: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d50380.23115567593!2d-4.83077196885619!3d37.88919102069347!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd6cdf676391abeb%3A0x264f694fec2cba90!2zQ8OzcmRvYmE!5e0!3m2!1ses!2ses!4v1762531376508!5m2!1ses!2ses',
  wedRadio: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d37751.15736575291!2d-4.888898951516481!3d37.87235651276212!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd6d27816af6147b%3A0xdd5872b23f40d3e!2sHuerta%2028!5e0!3m2!1ses!2ses!4v1762531094331!5m2!1ses!2ses',
}

const directions = {
  prewedRadio: 'Av. del Brillante, 83, Nte. Sierra, 14012 Córdoba',
  busRadio: props.t.busPickCordoba,
  wedRadio:'Ctra. Palma del Río, Km 6,5, 14005 Córdoba'
}



const iframeSrc = computed(() => mapUrls[selected.value])
</script>

<template>
  <section
    id="location"
    class="text-center bg-base-300 w-full flex flex-col justify-center items-center gap-3 h-fit p-5 pb-15 pt-5 px-5 md:px-10"
  >
  <h2 class="text-5xl text-secondary-content font-extrabold font-title pb-2">
    {{ props.t.locationTitle }}
  </h2>
  <div class="text-center w-full flex flex-col-reverse lg:flex-row-reverse justify-center items-center gap-5">
  <div class="w-full md:w-2/3 text-xl">
    <h2 class="text-4xl text-primary-content font-extrabold font-title pb-2">
      {{ props.t.locationSubtitle }}
    </h2>
    <div class="flex flex-col gap-5" v-html="props.t.locationInfo"></div>
    </div>
    <div class="w-full flex flex-col md:w-1/3 text-center justify-center items-center gap-3">
      <div class="join">
        <input
          class="join-item btn btn-xs sm:btn-sm md:btn-md"
          type="radio"
          name="options"
          :aria-label="props.t.prewedRadio"
          :checked="selected === 'prewedRadio'"
          @change="selected = 'prewedRadio'"
        />
        <input
          class="join-item btn btn-xs sm:btn-sm md:btn-md"
          type="radio"
          name="options"
          :aria-label="props.t.busRadio"
          :checked="selected === 'busRadio'"
          @change="selected = 'busRadio'"
        />
        <input
          class="join-item btn btn-xs sm:btn-sm md:btn-md"
          type="radio"
          name="options"
          :aria-label="props.t.wedRadio"
          :checked="selected === 'wedRadio'"
          @change="selected = 'wedRadio'"
        />
      </div>props.t.busPickCordoba
      <p v-if="selected === 'wedRadio' || selected === 'prewedRadio'" class="text-xl text-primary-content font-extrabold font-title pb-2">{{ directions[selected] }}</p>
      <p v-if="selected === 'busRadio'" class="text-xl text-primary-content font-extrabold font-title pb-2">{{ props.t.busPickCordoba }}</p>

      <iframe
        :src="iframeSrc"
        class="w-full md:h-96 rounded-xl"
        allowfullscreen
        loading="lazy"
        referrerpolicy="no-referrer-when-downgrade"
      ></iframe>
    </div>
  </div>
  </section>
  <LocationCarrousel />
</template>
