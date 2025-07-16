<script setup>
import { onMounted, ref } from 'vue'
import Countdown from './Countdown.vue'

const props = defineProps({
  t: Object
})


const carouselRef = ref(null)

onMounted(() => {
  const interval = 2000
  let currentIndex = 0

  const carouselEl = carouselRef.value
  const items = carouselEl.querySelectorAll('.carousel-item')
  const totalItems = items.length
  const itemHeight = items[0].offsetHeight

  setInterval(() => {
    currentIndex = (currentIndex + 1) % totalItems
    carouselEl.scrollTo({
      top: currentIndex * itemHeight,
      behavior: 'smooth',
    })
  }, interval)
})
</script>

<template>
  <section class="gap-3 px-2 md:px-8 bg-base-200 w-screen py-20 overflow-x-hidden min-h-fit h-auto">
    <div class="flex justify-center items-center gap-3 flex-col-reverse lg:flex-row-reverse">
      <div class="mask mask-squircle max-w-11/12 min-h-fit h-auto w-96">
        <div
        class="carousel carousel-vertical rounded-box h-96 w-96 overflow-hidden"
        ref="carouselRef"
      >
        <div class="carousel-item h-full">
          <img src="/start.webp" />
        </div>
        <div class="carousel-item h-full">
          <img src="/snow.webp" />
        </div>
        <div class="carousel-item h-full">
          <img src="/seville.webp" />
        </div>
        <div class="carousel-item h-full">
          <img src="/otters.webp" />
        </div>
        <div class="carousel-item h-full">
          <img src="/elegant.webp" />
        </div>
        <div class="carousel-item h-full">
          <img src="/huesca.webp" />
        </div>
      </div>
      </div>
      <div class="flex justify-center flex-col w-full md:pr-2 md:w-3/5">
        <h1 class="text-8xl font-bold text-center text-secondary-content font-title">{{ $props.t.title }}</h1>
        <h2 class="text-5xl font-semibold text-center font-title">{{ $props.t.subtitle }}</h2>
        <div class="py-6 text-center" v-html=$props.t.invitation></div>
        <Countdown :t="t" />
        <a href="https://forms.gle/ZxMq53erEwtdcxYBA" target="_blank" rel="noopener" class="btn btn-accent text-xl max-w-48 self-center mb-10">
          {{ $props.t.toForm }}
        </a>
      </div>
    </div>
  </section>
</template>
