---
clicks: 2
---
<script setup>
const subs = [
  'An analyst, a DataSHIELD server, and an OMOP CDM database.',
  '<strong>Plug &amp; play</strong> : dsOMOP connects with a resource — engine, url, user, password.',
  '<strong>dsOMOPClient</strong> orchestrates the request; <strong>dsOMOP</strong> runs the retrieval on the database.',
]
</script>
<div class="flex flex-col h-full" style="gap: 0.4rem;">
<h2 style="font-size: 1.08em; text-align: center;">Plug-and-play access to OMOP data</h2>
<div class="arch-sub"><transition name="regfade" mode="out-in"><span :key="Math.min($clicks, 2)" v-html="subs[Math.min($clicks, 2)]"></span></transition></div>
<div class="arch-stage">
<div class="arch-node"><svg width="42" height="34" viewBox="0 0 42 34"><circle cx="21" cy="11" r="7" fill="#5cebff" /><path d="M8 33 C8 23 34 23 34 33 Z" fill="#5cebff" /></svg><div class="arch-node-name">Analyst</div><div class="arch-badge client">dsOMOPClient</div></div>
<div class="arch-conn"><svg viewBox="0 0 120 80" width="120" height="80"><text class="arch-lbl" x="60" y="13" text-anchor="middle">orchestrate</text><line class="arch-arrow-line" :class="{ flow: $clicks >= 2 }" x1="6" y1="30" x2="106" y2="30" /><polygon class="arch-head" :class="{ 'flow-r': $clicks >= 2 }" points="106,25 116,30 106,35" /><line class="arch-arrow-line back" :class="{ flow: $clicks >= 2 }" x1="114" y1="52" x2="14" y2="52" /><polygon class="arch-head" :class="{ 'flow-l': $clicks >= 2 }" points="14,47 4,52 14,57" /><text class="arch-lbl" x="60" y="73" text-anchor="middle">data</text></svg></div>
<div class="arch-node"><svg width="38" height="36" viewBox="0 0 38 36"><rect x="4" y="3" width="30" height="9" rx="2" fill="none" stroke="#7fd6a3" stroke-width="1.6" /><circle cx="9" cy="7.5" r="1.5" fill="#7fd6a3" /><rect x="4" y="14" width="30" height="9" rx="2" fill="none" stroke="#7fd6a3" stroke-width="1.6" /><circle cx="9" cy="18.5" r="1.5" fill="#7fd6a3" /><rect x="4" y="25" width="30" height="9" rx="2" fill="none" stroke="#7fd6a3" stroke-width="1.6" /><circle cx="9" cy="29.5" r="1.5" fill="#7fd6a3" /></svg><div class="arch-node-name">DataSHIELD<br>server</div><div class="arch-badge server">dsOMOP</div></div>
<div class="arch-conn arch-conn-sd" :class="{ connected: $clicks >= 1 }"><svg viewBox="0 0 120 80" width="120" height="80"><path class="arch-cable" d="M4,40 H64" /><g class="arch-plug"><rect x="64" y="33" width="18" height="14" rx="3" /><rect x="82" y="36" width="7" height="2.6" rx="1.3" /><rect x="82" y="41.4" width="7" height="2.6" rx="1.3" /></g><path class="arch-socket" d="M97,31 V49 M97,40 H116" /><g class="arch-spark" stroke="#00D964" stroke-width="1.5" stroke-linecap="round"><line x1="91" y1="40" x2="96" y2="33" /><line x1="91" y1="40" x2="96" y2="47" /></g><text class="arch-lbl" x="60" y="73" text-anchor="middle">plug &amp; play</text></svg></div>
<div class="arch-node"><svg width="34" height="38" viewBox="0 0 34 38"><ellipse cx="17" cy="7" rx="14" ry="5.5" fill="none" stroke="#6cb0e0" stroke-width="1.8" /><path d="M3 7 V31 C3 34.5 31 34.5 31 31 V7" fill="none" stroke="#6cb0e0" stroke-width="1.8" /><path d="M3 16 C3 19 31 19 31 16" stroke="#6cb0e0" stroke-width="1.1" opacity="0.5" fill="none" /><path d="M3 23.5 C3 26.5 31 26.5 31 23.5" stroke="#6cb0e0" stroke-width="1.1" opacity="0.5" fill="none" /></svg><div class="arch-node-name">OMOP CDM</div><div class="arch-node-sub">PostgreSQL</div></div>
<div class="arch-resource" :class="{ show: $clicks >= 1 }"><div class="arch-res-title">resource</div><div class="arch-res-row"><span class="k">engine</span><span class="v">postgresql</span></div><div class="arch-res-row"><span class="k">url</span><span class="v">…:5432/omop_cdm</span></div><div class="arch-res-row"><span class="k">user</span><span class="v">researcher</span></div><div class="arch-res-row"><span class="k">password</span><span class="v">••••••••</span></div></div>
</div>
</div>
