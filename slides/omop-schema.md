---
clicks: 1
---
<script setup>
import cdm54 from '../assets/cdm54.png'
</script>
<div class="flex flex-col h-full items-center justify-center" style="gap: 0.7rem;">
<h2 style="font-size: 1.15em;">OMOP CDM Schema</h2>
<div class="cdm-frame zoom-vocab" :class="{ zoomed: $clicks >= 1 }">
<img :src="cdm54" class="cdm-img" />
</div>
</div>
