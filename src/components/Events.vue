<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
  t: Object
})

const prewedingLocation = '<b><a target="_blank" rel="noopener" href="https://maps.app.goo.gl/vSzNuMcGSGHp4r268">Kon-Q</a></b>'
const wedingLocation = '<b><a target="_blank" rel="noopener" href="https://maps.app.goo.gl/QLPZvYDtoridTG7dA">Huerta 28</a></b>'

const events = ref([
  { date: '10/02/2026', name: props.t.timeout },
  { date: '17/04/2026', name: props.t.prewed, place: prewedingLocation },
  { date: '18/04/2026', name: props.t.wed, place: wedingLocation },
])

watch(
  () => [props.t.prewed, props.t.wed, props.t.tba],
  () => {
    events.value = [
      { date: '10/02/2026', name: props.t.timeout },
      { date: '17/04/2026', name: props.t.prewed, place: prewedingLocation },
      { date: '18/04/2026', name: props.t.wed, place: wedingLocation }
    ]
  }
)

</script>

<template>
 <section id="events" class="bg-base-100 w-11/12 flex flex-col justify-center items-center gap-2 py-15 overflow-x-hidden min-h-fit h-auto">
  <h2 class="text-5xl w-full text-center text-secondary-content font-extrabold font-title pb-2">{{ $props.t.events }}<span class="pl-1 text-accent font-main">*</span></h2>
  <ul class="timeline timeline-vertical text-2xl">
  <li v-for="event in events">
    <hr v-if="events.indexOf(event) !== 0"/>
    <div class="timeline-start font-title mr-5">{{ event.date }}</div>
    <div class="timeline-middle">
      <i class="bi bi-circle-fill text-secondary"></i>
    </div>
    <div class="timeline-end timeline-box my-5 text-xl ml-3" v-html="`${event.place ? `${event.place} - `: ''}${ event.name }`"></div>
    <hr v-if="events.indexOf(event) !== events.length - 1"/>
  </li>
  </ul>
  <p class="flex flex-row items-center gap-2 w-full justify-center px-4"><span class="text-accent font-main text-5xl self-start">*</span><span class="text-lg" span v-html="t.eventsQuote"></span></p>
 </section>
</template>