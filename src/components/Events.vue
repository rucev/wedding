<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
  t: Object
})

const events = ref([
  {date: '17/04/2026', name: props.t.prewed, place: props.t.tba},
  {date: '18/04/2026', name: props.t.wed, place: 'Huerta 28'},
])

watch(
  () => [props.t.prewed, props.t.wed, props.t.tba],
  () => {
    events.value = [
      { date: '17/04/2026', name: props.t.prewed, place: props.t.tba },
      { date: '18/04/2026', name: props.t.wed, place: 'Huerta 28' }
    ]
  }
)

</script>

<template>
 <section id="events" class="bg-base-100 w-11/12 flex flex-col justify-center items-center gap-2 py-15 overflow-x-hidden">
  <h2 class="text-5xl text-secondary-content font-extrabold font-title pb-2">{{ $props.t.events }}</h2>
  <ul class="timeline timeline-vertical text-2xl">
  <li v-for="event in events">
    <hr v-if="events.indexOf(event) !== 0"/>
    <div class="timeline-start font-title">{{ event.date }}</div>
    <div class="timeline-middle">
      <i class="bi bi-circle-fill text-secondary"></i>
    </div>
    <div class="timeline-end timeline-box my-5 text-xl">{{`${event.place} - ${ event.name }`}}</div>
    <hr v-if="events.indexOf(event) !== events.length - 1"/>
  </li>
</ul>
 </section>
</template>