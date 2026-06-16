---
theme: default
title: dsOMOP Workshop
class: text-center
drawings:
  persist: false
transition: slide-left
colorSchema: dark
css: unocss
codeCopy: false
---

<script setup>
import logoDswb from './assets/logo-dswb.png'
import dsomopLogo from './assets/dsomop-logo.png'
import davidPhoto from './assets/david-sarrat.jpg'
import isglobal from './assets/logos/isglobal.png'
import aphrc from './assets/logos/aphrc.png'
import dgh from './assets/logos/dgh.png'
import iressef from './assets/logos/iressef.png'
import ahri from './assets/logos/ahri.png'
import datashield from './assets/logos/datashield.png'
import ohdsi from './assets/logos/ohdsi.png'

const row1 = [
  { src: isglobal, h: 26, alt: 'ISGlobal', url: 'https://www.isglobal.org' },
  { src: aphrc, h: 32, alt: 'APHRC', url: 'https://aphrc.org' },
  { src: ahri, h: 42, alt: 'AHRI', url: 'https://ahri.gov.et' },
  { src: dgh, h: 42, alt: 'Hôpital Général de Douala', url: 'https://www.facebook.com/hgdcam/' },
]
const row2 = [
  { src: iressef, h: 48, alt: 'IRESSEF', url: 'https://iressef.org' },
  { src: datashield, h: 30, alt: 'DataSHIELD', url: 'https://www.datashield.org' },
  { src: ohdsi, h: 32, alt: 'OHDSI', url: 'https://www.ohdsi.org' },
]
</script>

<div class="flex flex-col items-center justify-center h-full">
  <img :src="logoDswb" style="height: 80px; margin-bottom: 0.9em;" />
  <div class="flex items-center justify-center" style="font-family: 'Roboto Mono', monospace; font-weight: 700; font-size: 3.2em; color: #0A1119; gap: 0.28em;">
    <img :src="dsomopLogo" style="height: 1.3em;" />
    <span>dsOMOP&nbsp;Workshop</span>
  </div>
  <div class="flex flex-col items-center gap-1" style="margin-top: 1em;">
    <img :src="davidPhoto" style="width: 64px; height: 64px; border-radius: 50%; object-fit: cover; border: 2px solid rgba(0,0,0,0.15);" />
    <span style="font-family: 'Roboto Mono', monospace; font-size: 0.85em; color: #0A1119;">David Sarrat Gonz&aacute;lez</span>
  </div>
  <div class="logo-grid" style="margin-top: 1.6em;">
    <a v-for="p in row1" :key="p.alt" :href="p.url" target="_blank" rel="noopener" class="logo-badge">
      <img :src="p.src" :alt="p.alt" :style="{ height: p.h + 'px' }" />
    </a>
  </div>
  <div class="logo-grid" style="margin-top: 14px;">
    <a v-for="p in row2" :key="p.alt" :href="p.url" target="_blank" rel="noopener" class="logo-badge">
      <img :src="p.src" :alt="p.alt" :style="{ height: p.h + 'px' }" />
    </a>
  </div>
</div>

---
src: ./slides/cdm-section.md
---

---
src: ./slides/hospitals-datashield.md
---

---
src: ./slides/advantages-interop.md
---

---
src: ./slides/advantages-tools.md
---

---
src: ./slides/omop-section.md
---

---
src: ./slides/omop-perks.md
---

---
src: ./slides/omop-schema.md
---

---
src: ./slides/vocab-problem.md
---

---
src: ./slides/vocab-lookup.md
---

---
src: ./slides/athena-search.md
---

---
src: ./slides/omop-schema-clinical.md
---

---
src: ./slides/model-extensibility.md
---

---
src: ./slides/longitudinal-data.md
---

---
src: ./slides/closing.md
class: closing-slide
---
