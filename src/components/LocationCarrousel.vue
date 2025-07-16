<script setup>
import { onMounted, ref, onBeforeUnmount } from 'vue'

const carouselRef = ref(null)
let intervalId = null

onMounted(() => {
  const interval = 5000
  let currentIndex = 0

  const carouselEl = carouselRef.value
  const items = carouselEl.querySelectorAll('.carousel-item')
  const totalItems = items.length

  function scrollToIndex(index) {
    const itemWidth = items[0].offsetWidth
    carouselEl.scrollTo({
      left: index * itemWidth,
      behavior: 'smooth'
    })
  }

  intervalId = setInterval(() => {
    currentIndex = (currentIndex + 1) % totalItems
    scrollToIndex(currentIndex)
  }, interval)
})

onBeforeUnmount(() => {
  clearInterval(intervalId)
})
</script>

<template>
  <div class="overflow-hidden w-full">
    <div ref="carouselRef" class="carousel w-full overflow-x-auto scroll-smooth whitespace-nowrap">
      <div class="carousel-item w-full inline-block h-86">
        <img
          src="https://www.spain.info/export/sites/segtur/.content/imagenes/cabeceras-grandes/andalucia/patio-naranjos-catedral-cordoba-s624076895.jpg"
          class="w-full h-full object-cover"
          alt="1"
        />
      </div>
      <div class="carousel-item w-full inline-block h-86">
        <img
          src="https://www.mmms.de/c24/mezquita_cabecera_2020_1.jpg"
          class="w-full h-full object-cover"
          alt="2"
        />
      </div>
      <div class="carousel-item w-full inline-block h-86">
        <img
          src="https://images.mnstatic.com/01/6c/016c9f4752ca23d782d4612a2b6930df.jpg"
          class="w-full h-full object-cover"
          alt="3"
        />
      </div>
      <div class="carousel-item w-full inline-block h-86">
        <img
          src="https://xn--baosarabesdecordoba-w3b.com/wp-content/uploads/2023/05/Juderia.jpg"
          class="w-full h-full object-cover"
          alt="4"
        />
      </div>
            <div class="carousel-item w-full inline-block h-86">
        <img
          src="https://www.spain.info/export/sites/segtur/.content/imagenes/cabeceras-grandes/andalucia/alcazar-reyes-cordoba-s511384591.jpg"
          class="w-full h-full object-cover"
          alt="5"
        />
      </div>
    </div>
  </div>
</template>
