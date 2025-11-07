<script setup>
const props = defineProps({
  t: Object
})

</script>

<template>
  <section id="share" class="text-center w-full bg-base-100 flex flex-col justify-center items-center gap-5 min-h-fit h-auto bottom-0 relative py-10 px-3">
    <div className="divider"></div>  
    <h2 class="text-6xl text-secondary-content font-extrabold font-title pb-2">{{ $props.t.bookTitle }}</h2>
    <div class="text-xl flex flex-col gap-5 w-full md:w-3/4 lg:w-1/2" v-html=$props.t.bookText></div>
    <a href="https://forms.gle/viSNNzmSuPVTvcATA" target="_blank" rel="noopener" class="btn btn-secondary btn-md md:btn-xl">{{ $props.t.bookCta }}</a>
  </section>
</template>