<script setup>
import Hero from './components/Hero.vue'
import Story from './components/Story.vue'
import Place from './components/Place.vue'
import { ref, watch, onMounted } from 'vue'
import locales from './locales/index'
import Events from './components/Events.vue'
import History from './components/History.vue'
import Faq from './components/Faq.vue'
import Disclaimer from './components/Disclaimer.vue'

const locale = ref(null)
const t = ref(null)
const navLinks = ref(null)
const availableLocales = ref(['es', 'ca', 'en'].filter(_locale => _locale !== locale))

const getDefaultLocale = () => {
  const defaultLang = navigator.language.slice(0, 2)
  return defaultLang === 'es' || defaultLang === 'ca' ? defaultLang : 'en'
}

const setNavLinks = () => {
  const links = [
    {name: t.value.events, id: '#events'},
    {name: t.value.locationTitle, id: '#location'},
    {name: t.value.storyTitle, id: '#story'},
    {name: t.value.historyTitle, id: '#history'},
    {name: t.value.faq, id: '#faq'},
    {name: t.value.disclaimerTitle, id: '#disclaimer'},
  ]
  navLinks.value = links
}

const closeDrawer = () => {
  const drawerToggle = document.getElementById('my-drawer-3')
  if (drawerToggle) drawerToggle.checked = false
}

const changeLocale = (newLocale) => {
  locale.value = newLocale
}

onMounted(() => {
  if (!locale.value) {
    locale.value = getDefaultLocale()
  }
})

watch(locale, (newLocale) => {
  if (!newLocale) return

  document.documentElement.lang = newLocale

  if (newLocale === 'es') {
    t.value = locales.es
    availableLocales.value = ['ca', 'en']
  } else if (newLocale === 'ca') {
    t.value = locales.ca
    availableLocales.value = ['en', 'es']
  } else {
    t.value = locales.en
    availableLocales.value = ['es', 'ca']
  }
  setNavLinks()
})


</script>

<template>
  <div v-if="locale" class="w-screen overflow-hidden">
    <div class="drawer drawer-top z-20 fixed w-full">
      <input id="mobile-drawer" type="checkbox" class="drawer-toggle" />
      <div class="drawer-content flex flex-col">
        <div class="navbar bg-base-200 w-full justify-between">
          <label for="mobile-drawer" class="btn btn-square btn-ghost">
            <i class="bi bi-list text-2xl"></i>
          </label>
          <div>
            <div class="menu menu-horizontal">
              <div class="dropdown dropdown-bottom dropdown-end">
                <div tabindex="0" role="button" class="btn"><i class="bi bi-translate text-xl"></i></div>
                  <ul tabindex="0" class="dropdown-content menu bg-base-100 rounded-box z-1 w-52 p-2 shadow-sm">
                    <li v-for="_locale in availableLocales">
                      <button class="font-semibold" v-on:click="changeLocale(_locale)">{{ _locale === 'es' ? 'Español': _locale === 'en' ? 'English' : 'Català'}}</button>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
      </div>
      <div class="drawer-side w-full">
        <label for="mobile-drawer" class="drawer-overlay"></label>
        <ul class="menu p-4 w-full bg-base-200 text-base">
          <li v-for="link in navLinks" :key="link.id">
            <a :href="link.id" @click="closeDrawer('mobile-drawer')">{{ link.name }}</a>
          </li>
        </ul>
      </div>
    </div>
  </div>
  <Hero v-if="t" :t="t" />
  <Events v-if="t" :t="t"/>
  <Place v-if="t" :t="t"/>
  <Story v-if="t" :t="t"/>
  <History v-if="t" :t="t"/>
  <Faq v-if="t" :t="t" />
  <Disclaimer v-if="t" :t="t" />
</template>
