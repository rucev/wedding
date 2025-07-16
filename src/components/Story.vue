<script setup>
const props = defineProps({
  t: Object
})

</script>

<template>
  <section id="story" class="text-center w-full max-w-11/12 bg-base-100 flex flex-col-reverse md:flex-row justify-center items-center gap-5 h-auto min-h-[500px] py-10 pl-5">
    <div>
      <img src="/sleepy-otters.svg" class="w-60 h-60 md:h-96 md:w-96 rotate-45 animate-[spin_15s_infinite] self-center"/>
    </div>
    <div class="w-full md:w-1/2 text-xl">
      <h2 class="text-5xl text-secondary-content font-extrabold font-title pb-2">{{ $props.t.storyTitle }}</h2>
      <div class="flex flex-col gap-5" v-html="$props.t.storyDetails"></div>
    </div>
  </section>
</template>