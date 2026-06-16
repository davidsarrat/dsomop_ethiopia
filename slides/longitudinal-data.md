---
clicks: 3
---
<script setup>
const pidColor = '#2F80ED'
const conceptColor = '#00B04F'
const rows = [
  { step: 1, pid: '1234', cid: '4099154', cname: 'Body weight', value: '82 kg', date: '2021-06-10', dateColor: '#FEAE00' },
  { step: 2, pid: '1234', cid: '4099154', cname: 'Body weight', value: '79 kg', date: '2022-06-14', dateColor: '#FF6900' },
  { step: 3, pid: '1234', cid: '4099154', cname: 'Body weight', value: '77 kg', date: '2023-06-09', dateColor: '#ED1C24' },
]
</script>
<div class="flex flex-col h-full" style="gap: 0.45rem;">
<h2 style="font-size: 1.08em; text-align: center;">Longitudinal by design</h2>
<div class="reg-prompt"><transition name="regfade" mode="out-in"><span :key="$clicks === 0 ? 'i' : 'q'"><template v-if="$clicks === 0">The same person, tracked over time.</template><template v-else>Record another <strong>body-weight</strong> entry on a new date.</template></span></transition></div>
<div class="reg-stage">
<div class="reg-person"><div class="reg-avatar"><svg viewBox="0 0 120 120" width="74" height="74"><defs><linearGradient id="pgLon" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#2ee07f" /><stop offset="1" stop-color="#00B04F" /></linearGradient></defs><circle cx="60" cy="44" r="22" fill="url(#pgLon)" /><path d="M24 102 C24 78 41 68 60 68 C79 68 96 78 96 102 Z" fill="url(#pgLon)" /></svg></div><div class="reg-person-label">PERSON</div><div class="reg-pidchip">person_id = <span class="reg-hl" :style="{ color: pidColor, background: pidColor + '22' }">1234</span></div></div>
<div class="reg-tables">
<div class="reg-table"><div class="reg-tname">MEASUREMENT</div><div class="reg-head"><div class="reg-c c-pid">person_id</div><div class="reg-c c-cid">measurement_concept_id</div><div class="reg-c c-val">value_as_number</div><div class="reg-c c-date">measurement_date</div></div><template v-for="r in rows" :key="r.date"><div class="reg-row" v-if="$clicks >= r.step"><div class="reg-c c-pid"><span class="reg-pidv reg-hl" :style="{ color: pidColor, background: pidColor + '22' }">{{ r.pid }}</span></div><div class="reg-c c-cid"><span class="reg-cid reg-hl" :style="{ color: conceptColor, background: conceptColor + '22' }">{{ r.cid }}</span><span class="reg-cname">{{ r.cname }}</span></div><div class="reg-c c-val"><span>{{ r.value }}</span></div><div class="reg-c c-date"><span class="reg-datev reg-hl" :style="{ color: r.dateColor, background: r.dateColor + '22' }">{{ r.date }}</span></div></div></template></div>
</div>
</div>
<div class="reg-caption" v-if="$clicks >= 3">Same <strong style="color: #2F80ED;">person_id</strong>, same <strong style="color: #00B04F;">concept_id</strong>, different <strong style="color: #FF6900;">dates</strong> : a full clinical history.</div>
</div>
