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
  'Everything converges into one dataset — keyed by concept_id, with disclosure control.',
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
  { cid: 'gender_concept_id', nm: 'gender' },
  { cid: 'condition_concept_id', nm: 'condition' },
  { cid: 'drug_concept_id', nm: 'drug' },
  { cid: 'hba1c', nm: 'hba1c' },
]
const drows = [
  { pid: '1234', c: [{ id: '8532', t: 'Female' }, { id: '201826', t: 'Type 2 diabetes' }, { id: '1503297', t: 'Metformin' }, { id: '7.4', t: '7.4 %' }] },
  { pid: '1297', c: [{ id: '8507', t: 'Male' }, { id: '320128', t: 'Hypertension' }, { id: '1503297', t: 'Metformin' }, { id: '6.1', t: '6.1 %' }] },
  { pid: '1305', c: [{ id: '8532', t: 'Female' }, { id: '201826', t: 'Type 2 diabetes' }, { id: '1503297', t: 'Metformin' }, { id: '7.9', t: '7.9 %' }] },
  { pid: '1342', c: [{ id: '8507', t: 'Male' }, { id: '317009', t: 'Asthma' }, { id: '< 5', t: '< 5', supp: true }, { id: '5.6', t: '5.6 %' }] },
  { pid: '1358', c: [{ id: '8532', t: 'Female' }, { id: '320128', t: 'Hypertension' }, { id: '1503297', t: 'Metformin' }, { id: '6.4', t: '6.4 %' }] },
]
</script>
<div class="flex flex-col h-full" style="gap: 0.4rem;">
<h2 style="font-size: 1.08em; text-align: center;">dsOMOP removes the complexity</h2>
<div class="sx-stepper"><template v-for="(s, i) in steps" :key="s.n"><div class="sx-conn" :class="{ done: Math.min($clicks, 3) >= i }" v-if="i > 0"></div><div class="sx-step" :class="{ active: i === Math.min($clicks, 3), done: i < Math.min($clicks, 3) }"><span class="sx-num">{{ s.n }}</span><span class="sx-step-label">{{ s.label }}</span></div></template></div>
<div class="sx-cap">{{ titles[Math.min($clicks, 3)] }}</div>
<div class="sx-stage">
<transition name="sxfade" mode="out-in">
<div class="sx-panel" :key="Math.min($clicks, 3)">
<template v-if="Math.min($clicks, 3) === 0"><div class="sx-menu"><div><div class="sx-menu-h" style="color:#E5484D;">CONDITIONS</div><div class="sx-menu-item"><span>Type 2 diabetes</span><span class="dom">SNOMED</span></div><div class="sx-menu-item"><span>Hypertension</span><span class="dom">SNOMED</span></div><div class="sx-menu-item"><span>Asthma</span><span class="dom">SNOMED</span></div></div><div><div class="sx-menu-h" style="color:#8B5CF6;">DRUGS</div><div class="sx-menu-item"><span>Metformin</span><span class="dom">RxNorm</span></div><div class="sx-menu-item"><span>Insulin</span><span class="dom">RxNorm</span></div><div class="sx-menu-item"><span>Statins</span><span class="dom">RxNorm</span></div></div><div><div class="sx-menu-h" style="color:#00B04F;">MEASUREMENTS</div><div class="sx-menu-item"><span>Body weight</span><span class="dom">LOINC</span></div><div class="sx-menu-item"><span>HbA1c</span><span class="dom">LOINC</span></div><div class="sx-menu-item"><span>Blood pressure</span><span class="dom">LOINC</span></div></div><div><div class="sx-menu-h" style="color:#FEAE00;">OBSERVATIONS</div><div class="sx-menu-item"><span>Gender</span><span class="dom">SNOMED</span></div><div class="sx-menu-item"><span>Smoking status</span><span class="dom">LOINC</span></div><div class="sx-menu-item"><span>Marital status</span><span class="dom">SNOMED</span></div></div></div></template>
<template v-else-if="Math.min($clicks, 3) === 1"><div class="sx-charts"><div class="sx-chart"><div class="sx-chart-title">Age distribution</div><div class="sx-bars"><div class="sx-bar" v-for="(a, i) in ages" :key="i" :style="{ height: (a * 2.6) + 'px', background: '#5cebff' }"></div></div><div class="sx-xlab"><span v-for="(l, i) in ageLab" :key="i">{{ l }}</span></div></div><div class="sx-chart"><div class="sx-chart-title">Gender</div><div class="sx-gender"><div class="sx-gcol"><div class="sx-gbar" style="height:84px; background:#e5749b;"></div><div class="sx-glab">F 56%</div></div><div class="sx-gcol"><div class="sx-gbar" style="height:66px; background:#5b9fe0;"></div><div class="sx-glab">M 44%</div></div></div></div><div class="sx-chart"><div class="sx-chart-title">Most common conditions</div><div class="sx-hbars"><div class="sx-hbar" v-for="c in topc" :key="c.name"><span class="sx-hbar-lab">{{ c.name }}</span><div class="sx-hbar-fill" :style="{ width: (c.v * 2.6) + 'px', background: c.color }"></div></div></div></div></div></template>
<template v-else-if="Math.min($clicks, 3) === 2"><div class="sx-ds"><div class="sx-dh"><div class="sx-dc pid">person_id</div><div class="sx-dc cid" v-for="col in dcols" :key="col.cid">{{ col.cid }}</div></div><div class="sx-dr" v-for="r in drows" :key="r.pid"><div class="sx-dc pid">{{ r.pid }}</div><div class="sx-dc" v-for="(cell, j) in r.c" :key="j"><span v-if="cell.supp" class="sx-supp">{{ cell.id }}</span><span v-else>{{ cell.id }}</span></div></div></div><div class="sx-disc">🔒 <span><b>Disclosure control</b> : any subgroup with n &lt; 5 patients is blocked before it leaves the server.</span></div></template>
<template v-else><div class="sx-ds"><div class="sx-dh tr"><div class="sx-dc pid">person_id</div><div class="sx-dc nm" v-for="col in dcols" :key="col.nm">{{ col.nm }}</div></div><div class="sx-dr" v-for="r in drows" :key="r.pid"><div class="sx-dc pid">{{ r.pid }}</div><div class="sx-dc" v-for="(cell, j) in r.c" :key="j"><span v-if="cell.supp" class="sx-supp">{{ cell.t }}</span><span v-else class="sx-tr-v">{{ cell.t }}</span></div></div></div></template>
</div>
</transition>
</div>
</div>
