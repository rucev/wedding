<script setup>
const props = defineProps({
  t: Object
})

</script>

<template>
  <section id="history" class="text-center w-full bg-base-300 flex flex-col md:flex-row justify-center items-center gap-5 min-h-fit py-10 px-10">
    <div class="text-xl w-full md:w-1/2 px-5">
      <h2 class="text-5xl text-secondary-content font-extrabold font-title pb-2">{{ $props.t.historyTitle }}</h2>
      <div class="flex flex-col gap-5" v-html="$props.t.historyDetails"></div>
    </div>
    <div class="w-full md:w-1/2 px-10">
      <img src="https://www.igualdad.gob.es/wp-content/uploads/2025/06/POSTER-A4-002-scaled.jpg" class="w-full h-fit rounded-4xl"/>
    </div>
  </section>
</template>