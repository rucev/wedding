<script setup>
const props = defineProps({
  t: Object
})

</script>

<template>
  <section id="disclaimer" class="text-center w-full bg-base-300 flex flex-col-reverse md:flex-row justify-center items-center gap-5 min-h-fit bottom-0 relative py-10 px-3">
    <div>
      <img src="https://i.imgur.com/qOt3QRk.gif" class="rounded-xl"/>
    </div>
    <div class="w-full md:w-1/2">
      <h2 class="text-6xl text-secondary-content font-extrabold font-title pb-2">{{ $props.t.disclaimerTitle }}</h2>
      <div class="text-3xl flex flex-col gap-5">{{ $props.t.disclaimerContent }}</div>
    </div>
  </section>
</template>