---
clicks: 12
---
<script setup>
const prompts = ['a varicella diagnosis', 'a type 2 diabetes diagnosis', 'a body-weight measurement', 'an HbA1c measurement', 'a smoking-status observation', 'a marital-status observation']
const PID = '#2F80ED'
const tables = [
  { name: 'CONDITION_OCCURRENCE', hasValue: false, headers: ['person_id', 'condition_concept_id', 'condition_start_date'], rows: [
    { c: 2, pid: '1234', cid: '434272', cname: 'Varicella', color: '#E5484D', date: '2023-03-14' },
    { c: 4, pid: '1234', cid: '201826', cname: 'Type 2 diabetes mellitus', color: '#F2710A', date: '2023-05-02' },
  ] },
  { name: 'MEASUREMENT', hasValue: true, headers: ['person_id', 'measurement_concept_id', 'value_as_number', 'measurement_date'], rows: [
    { c: 6, pid: '1234', cid: '4099154', cname: 'Body weight', color: '#00B04F', value: '78 kg', date: '2023-05-02' },
    { c: 8, pid: '1234', cid: '4184637', cname: 'Hemoglobin A1c', color: '#0EA5C0', value: '7.4 %', date: '2023-05-02' },
  ] },
  { name: 'OBSERVATION', hasValue: true, headers: ['person_id', 'observation_concept_id', 'value_as_concept_id', 'observation_date'], rows: [
    { c: 10, pid: '1234', cid: '43054909', cname: 'Tobacco smoking status', color: '#8B5CF6', vcid: '45883458', vname: 'Former smoker', date: '2023-04-18' },
    { c: 12, pid: '1234', cid: '4053609', cname: 'Marital status', color: '#E5439B', vcid: '4338692', vname: 'Married', date: '2023-04-18' },
  ] },
]
</script>
<div class="flex flex-col h-full" style="gap: 0.45rem;">
<h2 style="font-size: 1.08em; text-align: center;">One model, endlessly extensible</h2>
<div class="reg-prompt"><transition name="regfade" mode="out-in"><span :key="$clicks === 0 ? 'i' : Math.floor(($clicks - 1) / 2)"><template v-if="$clicks === 0">Pick any clinical fact, map it to a standard concept, store it.</template><template v-else>What if we want to register <strong>{{ prompts[Math.floor(($clicks - 1) / 2)] }}</strong>?</template></span></transition></div>
<div class="reg-stage">
<div class="reg-person"><div class="reg-avatar"><svg viewBox="0 0 120 120" width="74" height="74"><defs><linearGradient id="pgExt" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#2ee07f" /><stop offset="1" stop-color="#00B04F" /></linearGradient></defs><circle cx="60" cy="44" r="22" fill="url(#pgExt)" /><path d="M24 102 C24 78 41 68 60 68 C79 68 96 78 96 102 Z" fill="url(#pgExt)" /></svg></div><div class="reg-person-label">PERSON</div><div class="reg-pidchip">person_id = <span class="reg-hl" :style="{ color: PID, background: PID + '22' }">1234</span></div></div>
<div class="reg-tables">
<template v-for="t in tables" :key="t.name"><div class="reg-table" v-if="$clicks >= t.rows[0].c"><div class="reg-tname">{{ t.name }}</div><div class="reg-head"><div class="reg-c c-pid">person_id</div><div class="reg-c c-cid">{{ t.headers[1] }}</div><div class="reg-c c-val" v-if="t.hasValue">{{ t.headers[2] }}</div><div class="reg-c c-date">{{ t.hasValue ? t.headers[3] : t.headers[2] }}</div></div><template v-for="r in t.rows" :key="r.cid"><div class="reg-row" v-if="$clicks >= r.c"><div class="reg-c c-pid"><span class="reg-pidv reg-hl" :style="{ color: PID, background: PID + '22' }">{{ r.pid }}</span></div><div class="reg-c c-cid"><span class="reg-cid reg-hl" :style="{ color: r.color, background: r.color + '22' }">{{ r.cid }}</span><span class="reg-cname">{{ r.cname }}</span></div><div class="reg-c c-val" v-if="t.hasValue"><template v-if="r.vcid"><span class="reg-cid2">{{ r.vcid }}</span><span class="reg-cname">{{ r.vname }}</span></template><template v-else><span class="reg-val">{{ r.value }}</span></template></div><div class="reg-c c-date"><span class="reg-datev">{{ r.date }}</span></div></div></template></div></template>
</div>
</div>
<div class="reg-caption">Every fact is just a row keyed by a <strong style="color: #00B04F;">concept_id</strong> : the schema never changes.</div>
</div>
