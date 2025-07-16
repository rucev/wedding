<script setup>
const props = defineProps({
  t: Object
})

</script>

<template>
  <section id="faq" class="text-center w-full bg-base-100 flex flex-col justify-center items-center gap-5 min-h-fit h-[700px] py-10 px-10 z-0">
    <h2 class="text-5xl text-secondary-content font-extrabold font-title pb-2">{{ $props.t.faq }}</h2>
    <div v-for="faq in props.t.faqContent" class="collapse collapse-arrow bg-base-100 border border-base-300 w-full md:w-1/2">
      <input type="radio" name="my-accordion-2" />
      <div class="collapse-title font-semibold text-xl">{{ faq.q }}</div>
      <div class="collapse-content text-xl">{{ faq.a }}</div>
    </div>
  </section>
</template>