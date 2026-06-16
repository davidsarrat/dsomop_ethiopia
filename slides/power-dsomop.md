---
clicks: 3
---
<script setup>
const bins = ['<40', '40s', '50s', '60s', '70s', '80+']
const sites = [
  { name: 'Nairobi', loc: 'Kenya', color: '#00B04F', counts: [6, 14, 22, 18, 9, 3], step: 1 },
  { name: 'Douala', loc: 'Cameroon', color: '#FEAE00', counts: [4, 11, 19, 24, 14, 5], step: 2 },
  { name: 'Dakar', loc: 'Senegal', color: '#FF6900', counts: [3, 9, 16, 21, 17, 7], step: 3 },
]
const SCALE = 3
const MINI = 1.5
function pooledN(clicks) {
  return sites.filter(s => clicks >= s.step).reduce((a, s) => a + s.counts.reduce((x, y) => x + y, 0), 0)
}
</script>
<div class="flex flex-col h-full" style="gap: 0.4rem;">
<h2 style="font-size: 1.08em; text-align: center;">The power of dsOMOP</h2>
<div class="pow-sub">Same OMOP variables at every site, so the histogram bins line up and aggregates can be <strong>pooled</strong>.</div>
<div class="pow-stage">
<div class="pow-sites">
<template v-for="s in sites" :key="s.name"><div class="pow-site" :class="{ on: $clicks >= s.step }"><div class="pow-site-head"><span class="pow-site-name" :style="{ color: s.color }">{{ s.name }}</span><span class="pow-site-n">{{ s.loc }} · n={{ s.counts.reduce((a, b) => a + b, 0) }}</span></div><div class="pow-mini"><div class="pow-mini-bar" v-for="(c, i) in s.counts" :key="i" :style="{ height: (c * MINI) + 'px', background: s.color }"></div></div></div></template>
</div>
<div class="pow-merge"><div class="pow-arrow">→</div><div>pool counts</div></div>
<div class="pow-combined">
<div class="pow-combined-title">Age at T2D diagnosis · <span class="n">n={{ pooledN($clicks) }}</span></div>
<div class="pow-bars">
<template v-for="(b, i) in bins" :key="i"><div class="pow-col"><div class="pow-seg" v-for="s in sites" :key="s.name" :style="{ height: ($clicks >= s.step ? s.counts[i] * SCALE : 0) + 'px', background: s.color }"></div></div></template>
</div>
<div class="pow-xaxis"><div class="pow-xlabel" v-for="(b, i) in bins" :key="i">{{ b }}</div></div>
<div class="pow-legend"><span v-for="s in sites" :key="s.name"><span class="pow-dot" :style="{ background: s.color }"></span>{{ s.name }}</span></div>
</div>
</div>
<div class="pow-caption" v-if="$clicks >= 3">Patient records never leave each site : <strong style="color:#FEAE00;">DataSHIELD</strong> shares only per-bin counts, and <strong style="color:#00B04F;">OMOP</strong> makes them line up.</div>
</div>
