<script setup>
import ohdsi from '../assets/logos/ohdsi.png'
</script>
<div class="flex flex-col h-full items-center justify-center" style="gap: 0.5rem;">
<div class="logo-badge" style="height: 52px;"><img :src="ohdsi" style="height: 28px;" /></div>
<div class="omop-name"><b>O</b>bservational <b>M</b>edical <b>O</b>utcomes <b>P</b>artnership<br/><b>C</b>ommon <b>D</b>ata <b>M</b>odel</div>
<div class="omop-acr" style="font-size: 1.45em;">(OMOP CDM)</div>
<div class="perk-grid" style="margin-top: 0.7rem;">
<div class="perk-card" v-click><div class="perk-check">✓</div><div class="perk-text">All kinds of clinical research</div></div>
<div class="perk-card" v-click><div class="perk-check">✓</div><div class="perk-text">Interdisciplinary &amp; collaborative</div></div>
<div class="perk-card" v-click><div class="perk-check">✓</div><div class="perk-text">Public, open-source</div></div>
<div class="perk-card" v-click><div class="perk-check">✓</div><div class="perk-text">Community-developed tools</div></div>
<div class="perk-card span2" v-click><div class="perk-check">✓</div><div><div class="perk-text">Widely extended</div><div class="perk-sub">~1 billion patient records across 49 countries</div></div></div>
</div>
</div>
