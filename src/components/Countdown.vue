<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const props = defineProps({
  t: Object
})

const countdown = ref({
  days: 0,
  hours: 0,
  minutes: 0,
  seconds: 0
})

let intervalId

function updateCountdown() {
  const targetDate = new Date('2026-04-18T10:00:00Z')
  const now = new Date()
  const diff = targetDate - now

  if (diff <= 0) {
    countdown.value = { days: 0, hours: 0, minutes: 0, seconds: 0 }
    clearInterval(intervalId)
    return
  }

  const totalSeconds = Math.floor(diff / 1000)
  countdown.value = {
    days: Math.floor(totalSeconds / (3600 * 24)),
    hours: Math.floor((totalSeconds % (3600 * 24)) / 3600),
    minutes: Math.floor((totalSeconds % 3600) / 60),
    seconds: totalSeconds % 60
  }
}

onMounted(() => {
  updateCountdown()
  intervalId = setInterval(updateCountdown, 1000)
})

onBeforeUnmount(() => {
  clearInterval(intervalId)
})
</script>

<template>
  <div class="text-center mb-5">
    <div class="text-xl font-bold">
      <span>{{`${countdown.days} ${t.days} ` }}</span>
      <span>{{ `${countdown.hours} ${t.hours} ` }}</span>
      <span>{{ `${countdown.minutes} ${t.minAnd} ` }} </span>
      <span>{{ `${countdown.seconds} ${t.sec}`}} </span>
    </div>
  </div>
</template>
