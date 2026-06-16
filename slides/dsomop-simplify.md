---
clicks: 3
---
<script setup>
const steps = [
  { n: 1, label: 'Concept catalog' },
  { n: 2, label: 'Preview the data' },
  { n: 3, label: 'One dataset' },
  { n: 4, label: 'Readable names' },
]
const titles = [
  'Browse a catalog of the concepts available at the site, like a menu.',
  'Preview the cohort at a glance before pulling anything.',
  'Everything converges into one dataset — columns are concept_ids, with disclosure control.',
  'dsOMOP translates the concept_ids into readable text.',
]
const ages = [8, 18, 30, 26, 14, 6]
const ageLab = ['<40', '40s', '50s', '60s', '70s', '80+']
const topc = [
  { name: 'Hypertension', v: 38, color: '#FF6900' },
  { name: 'Type 2 diabetes', v: 29, color: '#E5484D' },
  { name: 'Asthma', v: 17, color: '#FEAE00' },
  { name: 'Varicella', v: 9, color: '#8B5CF6' },
]
const dcols = [
  { cid: '4184637', nm: 'hba1c' },
  { cid: '43054909', nm: 'smoking_status' },
  { cid: '201826', nm: 'type_2_diabetes' },
]
const dropCol = { cid: '441267', nm: 'cystic_fibrosis' }
const drows = [
  { pid: '1234', cells: [{ id: '7.4', t: '7.4' }, { id: '45883458', t: 'Former smoker' }, { id: '1', t: '1' }] },
  { pid: '1297', cells: [{ id: '6.1', t: '6.1' }, { id: '45879404', t: 'Never smoker' }, { id: '0', t: '0' }] },
  { pid: '1305', cells: [{ id: '7.9', t: '7.9' }, { id: '45883458', t: 'Former smoker' }, { id: '1', t: '1' }] },
  { pid: '1342', cells: [{ id: '5.6', t: '5.6' }, { id: '45881517', t: 'Current smoker' }, { id: '0', t: '0' }] },
  { pid: '1358', cells: [{ id: '6.4', t: '6.4' }, { id: '45879404', t: 'Never smoker' }, { id: '1', t: '1' }] },
]
</script>
<div class="flex flex-col h-full" style="gap: 0.4rem;">
<h2 style="font-size: 1.08em; text-align: center;">dsOMOP removes the complexity</h2>
<div class="sx-stepper"><template v-for="(s, i) in steps" :key="s.n"><div class="sx-conn" :class="{ done: $clicks >= i }" v-if="i > 0"></div><div class="sx-step" :class="{ active: i === $clicks, done: i < $clicks }"><span class="sx-num">{{ s.n }}</span><span class="sx-step-label">{{ s.label }}</span></div></template></div>
<div class="sx-cap">{{ titles[$clicks] }}</div>
<div class="sx-stage">
<transition name="sxfade" mode="out-in">
<div class="sx-panel" :key="$clicks <= 1 ? String($clicks) : 'tbl'">
<template v-if="$clicks === 0"><div class="sx-menu"><div><div class="sx-menu-h" style="color:#E5484D;">CONDITIONS</div><div class="sx-menu-item"><span>Type 2 diabetes</span><span class="dom">SNOMED</span></div><div class="sx-menu-item"><span>Hypertension</span><span class="dom">SNOMED</span></div><div class="sx-menu-item"><span>Asthma</span><span class="dom">SNOMED</span></div></div><div><div class="sx-menu-h" style="color:#8B5CF6;">DRUGS</div><div class="sx-menu-item"><span>Metformin</span><span class="dom">RxNorm</span></div><div class="sx-menu-item"><span>Insulin</span><span class="dom">RxNorm</span></div><div class="sx-menu-item"><span>Statins</span><span class="dom">RxNorm</span></div></div><div><div class="sx-menu-h" style="color:#00B04F;">MEASUREMENTS</div><div class="sx-menu-item"><span>Body weight</span><span class="dom">LOINC</span></div><div class="sx-menu-item"><span>HbA1c</span><span class="dom">LOINC</span></div><div class="sx-menu-item"><span>Blood pressure</span><span class="dom">LOINC</span></div></div><div><div class="sx-menu-h" style="color:#FEAE00;">OBSERVATIONS</div><div class="sx-menu-item"><span>Gender</span><span class="dom">SNOMED</span></div><div class="sx-menu-item"><span>Smoking status</span><span class="dom">LOINC</span></div><div class="sx-menu-item"><span>Marital status</span><span class="dom">SNOMED</span></div></div></div></template>
<template v-else-if="$clicks === 1"><div class="sx-charts"><div class="sx-chart"><div class="sx-chart-title">Age distribution</div><div class="sx-bars"><div class="sx-bar" v-for="(a, i) in ages" :key="i" :style="{ height: (a * 2.6) + 'px', background: '#5cebff' }"></div></div><div class="sx-xlab"><span v-for="(l, i) in ageLab" :key="i">{{ l }}</span></div></div><div class="sx-chart"><div class="sx-chart-title">Gender</div><div class="sx-gender"><div class="sx-gcol"><div class="sx-gbar" style="height:84px; background:#e5749b;"></div><div class="sx-glab">F 56%</div></div><div class="sx-gcol"><div class="sx-gbar" style="height:66px; background:#5b9fe0;"></div><div class="sx-glab">M 44%</div></div></div></div><div class="sx-chart"><div class="sx-chart-title">Most common conditions</div><div class="sx-hbars"><div class="sx-hbar" v-for="c in topc" :key="c.name"><span class="sx-hbar-lab">{{ c.name }}</span><div class="sx-hbar-fill" :style="{ width: (c.v * 2.6) + 'px', background: c.color }"></div></div></div></div></div></template>
<template v-else><div class="sx-ds"><div class="sx-dh" :class="{ tr: $clicks >= 3 }"><div class="sx-dc pid">person_id</div><div class="sx-dc" v-for="col in dcols" :key="col.cid"><transition name="cellsub" mode="out-in"><span :key="$clicks >= 3" :class="$clicks >= 3 ? 'nm' : 'cid'">{{ $clicks >= 3 ? col.nm : col.cid }}</span></transition></div><div class="sx-dc drop"><span class="sx-strk">{{ $clicks >= 3 ? dropCol.nm : dropCol.cid }}</span><span class="sx-droptag">n&lt;filter</span></div></div><div class="sx-dr" v-for="r in drows" :key="r.pid"><div class="sx-dc pid">{{ r.pid }}</div><div class="sx-dc" v-for="(cell, j) in r.cells" :key="j"><transition name="cellsub" mode="out-in"><span :key="$clicks >= 3" :class="{ 'sx-cidv': $clicks < 3 && cell.id !== cell.t, 'sx-trv': $clicks >= 3 && cell.id !== cell.t }">{{ $clicks >= 3 ? cell.t : cell.id }}</span></transition></div><div class="sx-dc drop"><span class="sx-strk">—</span></div></div></div><div class="sx-disc">🔒 <span><b>Disclosure control</b> : a variable recorded for fewer than 5 patients (<b>cystic_fibrosis</b>, n&lt;filter) is dropped before the dataset leaves the server.</span></div></template>
</div>
</transition>
</div>
</div>
