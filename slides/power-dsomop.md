---
clicks: 3
---
<script setup>
const sites = [
  { name: 'Nairobi', x: 17, color: '#00B04F', counts: [6, 14, 22, 18, 9, 3] },
  { name: 'Douala', x: 50, color: '#FEAE00', counts: [4, 11, 19, 24, 14, 5] },
  { name: 'Dakar', x: 83, color: '#FF6900', counts: [3, 9, 16, 21, 17, 7] },
]
const SCALE = 0.82
const MINI = 1.05
const subs = [
  'One analyst, three OMOP CDM sites.',
  '<strong>1 script 4 all</strong> : the same query reaches every site.',
  'Each site computes the histogram locally : patient data never moves.',
  'Only aggregates return : DataSHIELD pools them into one result.',
]
const total = sites.reduce((a, s) => a + s.counts.reduce((x, y) => x + y, 0), 0)
</script>
<div class="flex flex-col h-full" style="gap: 0.4rem;">
<h2 style="font-size: 1.08em; text-align: center;">The power of dsOMOP</h2>
<div class="fed-sub"><transition name="regfade" mode="out-in"><span :key="Math.min($clicks, 3)" v-html="subs[Math.min($clicks, 3)]"></span></transition></div>
<div class="fed-stage">
<svg class="fed-lines" viewBox="0 0 100 100" preserveAspectRatio="none">
<path class="fed-line fed-up" :class="{ show: $clicks >= 1 && $clicks < 3 }" d="M50,67 C42,52 25,40 17,29" /><path class="fed-line fed-up" :class="{ show: $clicks >= 1 && $clicks < 3 }" d="M50,67 L50,29" /><path class="fed-line fed-up" :class="{ show: $clicks >= 1 && $clicks < 3 }" d="M50,67 C58,52 75,40 83,29" />
<path class="fed-line fed-down" :class="{ show: $clicks >= 3 }" d="M17,29 C25,40 42,52 50,67" /><path class="fed-line fed-down" :class="{ show: $clicks >= 3 }" d="M50,29 L50,67" /><path class="fed-line fed-down" :class="{ show: $clicks >= 3 }" d="M83,29 C75,40 58,52 50,67" />
</svg>
<template v-for="s in sites" :key="s.name"><div class="fed-node" :class="{ compute: $clicks >= 2 }" :style="{ left: s.x + '%', top: '1%' }"><div class="fed-node-icon"><svg width="14" height="16" viewBox="0 0 14 16" fill="none"><ellipse cx="7" cy="3" rx="6" ry="2.4" :stroke="s.color" stroke-width="1.3" /><path d="M1 3 V13 C1 14.4 13 14.4 13 13 V3" :stroke="s.color" stroke-width="1.3" /><path d="M1 8 C1 9.4 13 9.4 13 8" :stroke="s.color" stroke-width="1.1" opacity="0.55" /></svg><span class="fed-node-name" :style="{ color: s.color }">{{ s.name }}</span></div><div class="fed-node-omop">OMOP CDM · n={{ s.counts.reduce((a, b) => a + b, 0) }}</div><div class="fed-mini"><div class="fed-mini-bar" v-for="(c, i) in s.counts" :key="i" :style="{ height: ($clicks >= 2 ? c * MINI : 0) + 'px', background: s.color }"></div></div><div class="fed-run">computed locally</div></div></template>
<div class="fed-tag" :class="{ show: $clicks >= 1 && $clicks < 3 }">1 script 4 all</div>
<div class="fed-client"><div class="fed-monitor"><div class="fed-script"><span class="cm"># one script, every site</span><br><span class="fn">ds.glm</span>(t2d <span class="kw">~</span> age + sex)</div><div class="fed-bars"><template v-for="i in 6" :key="i"><div class="fed-col"><div class="fed-seg" v-for="s in sites" :key="s.name" :style="{ height: ($clicks >= 3 ? s.counts[i - 1] * SCALE : 0) + 'px', background: s.color }"></div></div></template></div><div class="fed-pooled-label" :class="{ show: $clicks >= 3 }">pooled result · n={{ total }}</div></div><div class="fed-client-label">Analyst <span class="role">· R / DataSHIELD client</span></div></div>
</div>
</div>
