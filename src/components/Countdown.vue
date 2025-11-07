<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const props = defineProps({ t: Object })

const countdown = ref({
  days: 0,
  hours: 0,
  minutes: 0,
  seconds: 0
})

let intervalId

const updateCountdown = () => {
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
  <div class="grid grid-flow-col gap-5 text-center auto-cols-max w-[full] justify-center">
    <div class="flex flex-col font-mono text-center text-xs md:text-sm w-[4em] md:w-[6em]">
      <span class="countdown mx-auto text-center text-2xl md:text-5xl">
        <span
        class="text-center"
          :style="{ '--value': String(countdown.days) }"
        ></span>
      </span>
      {{ t.days }}
    </div>
    <div class="flex flex-col font-mono text-center text-xs md:text-sm w-[4em] md:w-[6em]">
      <span class="countdown mx-auto text-center text-2xl md:text-5xl">
        <span
        class="text-center"
          :style="{ '--value': String(countdown.hours) }"
        ></span>
      </span>
      {{ t.hours }}
    </div>

    <div class="flex flex-col font-mono text-center text-xs md:text-sm w-[4em] md:w-[6em]">
      <span class="countdown mx-auto text-center text-2xl md:text-5xl">
        <span
          :style="{ '--value': String(countdown.minutes) }"
        ></span>
      </span>
      {{ t.min }}
    </div>

    <div class="flex flex-col text-center text-xs md:text-sm w-[4em] md:w-[6em]">
      <span class="countdown mx-auto font-mono text-center text-2xl md:text-5xl">
        <span
          :style="{ '--value': String(countdown.seconds) }"
        ></span>
      </span>
      {{ t.sec }}
    </div>
  </div>
</template>
