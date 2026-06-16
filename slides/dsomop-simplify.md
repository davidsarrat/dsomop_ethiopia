---
clicks: 3
---
<script setup>
const subs = [
  'Browse a catalog of the concepts available at the site.',
  'Under the hood: many tables, all keyed by <strong>concept_id</strong>, joined on person.',
  'dsOMOP merges them into one dataset, tailored to the concepts you picked.',
  'And it translates the <strong>concept_ids</strong> into readable <strong>names</strong>.',
]
const cols = [
  { cid: '201826', name: 'type_2_diabetes' },
  { cid: '1503297', name: 'metformin' },
  { cid: '4099154', name: 'body_weight' },
  { cid: '4184637', name: 'hba1c' },
]
const rows = [
  { pid: '1234', vals: ['Yes', 'Yes', '78 kg', '7.4 %'] },
  { pid: '1297', vals: ['No', 'Yes', '81 kg', '6.8 %'] },
]
</script>
<div class="flex flex-col h-full" style="gap: 0.4rem;">
<h2 style="font-size: 1.08em; text-align: center;">dsOMOP removes the complexity</h2>
<div class="sim-sub"><transition name="regfade" mode="out-in"><span :key="Math.min($clicks, 3)" v-html="subs[Math.min($clicks, 3)]"></span></transition></div>
<div class="sim-catalog"><span class="sim-cat-label">Concept catalog</span><span class="sim-group"><span class="dom">Conditions</span> ▸ <b>Type 2 diabetes</b> · Varicella</span><span class="sim-group"><span class="dom">Drugs</span> ▸ <b>Metformin</b> · Insulin</span><span class="sim-group"><span class="dom">Measurements</span> ▸ <b>Body weight</b> · <b>HbA1c</b></span></div>
<div class="sim-stage">
<div class="sim-tables" :class="{ show: $clicks >= 1 }">
<div class="sim-table"><div class="sim-tname">condition_occurrence</div><div class="sim-thead"><div class="sim-tc sim-c1">person_id</div><div class="sim-tc sim-c2">condition_concept_id</div></div><div class="sim-trow"><div class="sim-tc sim-c1 sim-pid">1234</div><div class="sim-tc sim-c2 sim-cid" style="color: #F2710A;">201826</div></div></div>
<div class="sim-table"><div class="sim-tname">drug_exposure</div><div class="sim-thead"><div class="sim-tc sim-c1">person_id</div><div class="sim-tc sim-c2">drug_concept_id</div></div><div class="sim-trow"><div class="sim-tc sim-c1 sim-pid">1234</div><div class="sim-tc sim-c2 sim-cid" style="color: #8B5CF6;">1503297</div></div></div>
<div class="sim-table"><div class="sim-tname">measurement</div><div class="sim-thead"><div class="sim-tc sim-c1">person_id</div><div class="sim-tc sim-c2">measurement_concept_id</div><div class="sim-tc sim-c3">value</div></div><div class="sim-trow"><div class="sim-tc sim-c1 sim-pid">1234</div><div class="sim-tc sim-c2 sim-cid" style="color: #00B04F;">4099154</div><div class="sim-tc sim-c3">78</div></div></div>
</div>
<div class="sim-arrow" :class="{ show: $clicks >= 2 }"><svg width="46" height="20" viewBox="0 0 46 20"><line x1="2" y1="10" x2="36" y2="10" stroke="#FEAE00" stroke-width="2" /><polygon points="36,5 44,10 36,15" fill="#FEAE00" /></svg><span class="lbl">merge</span></div>
<div class="sim-dataset" :class="{ show: $clicks >= 2 }"><div class="sim-ds-title">Your dataset · one row per person</div><div class="sim-ds-table"><div class="sim-ds-head"><div class="sim-ds-c pid">person_id</div><div class="sim-ds-c" v-for="col in cols" :key="col.cid"><transition name="regfade" mode="out-in"><span :key="$clicks >= 3" :class="$clicks >= 3 ? 'name' : 'cid'">{{ $clicks >= 3 ? col.name : col.cid }}</span></transition></div></div><div class="sim-ds-row" v-for="r in rows" :key="r.pid"><div class="sim-ds-c pid">{{ r.pid }}</div><div class="sim-ds-c" v-for="(v, i) in r.vals" :key="i">{{ v }}</div></div></div></div>
</div>
</div>
