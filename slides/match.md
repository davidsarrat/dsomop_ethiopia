<script setup>
import datashield from '../assets/logos/datashield.png'
import ohdsi from '../assets/logos/ohdsi.png'
</script>

<div class="match-stage">
<div class="match-title">It's a match!</div>
<div class="match-photos">
<div class="ava ava-left"><img :src="datashield" alt="DataSHIELD" /></div>
<div class="ava ava-right"><img :src="ohdsi" alt="OHDSI / OMOP CDM" /></div>
</div>
<div class="match-sub">Federated analysis from DataSHIELD, harmonised data from the OMOP CDM : one script runs everywhere, and patient data never moves.</div>
</div>

<style>
.match-slide.slidev-layout { background: linear-gradient(135deg, #ff7854 0%, #ff5864 50%, #fd267a 100%) !important; color: #fff; }
.match-slide.slidev-layout::after { opacity: 0; }

.match-stage { height: 100%; display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 1.5rem; overflow: hidden; }

.match-title {
  font-family: 'Kaushan Script', cursive; font-size: 5em; line-height: 1; color: #fff;
  text-shadow: 0 3px 18px rgba(0, 0, 0, 0.25);
  animation: matchTitle 0.65s cubic-bezier(0.34, 1.56, 0.64, 1) 0.2s both;
}
@keyframes matchTitle { from { opacity: 0; transform: translateY(-22px) scale(0.7) rotate(-3deg); } to { opacity: 1; transform: none; } }

.match-photos { position: relative; width: 470px; height: 190px; }
.ava {
  position: absolute; top: 50%; left: 50%; width: 168px; height: 168px; margin: -84px 0 0 -84px;
  border-radius: 50%; background: #fff; border: 4px solid #fff; box-shadow: 0 10px 30px rgba(0, 0, 0, 0.28);
  display: flex; align-items: center; justify-content: center;
}
.ava img { width: 78%; height: 78%; object-fit: contain; }
.ava-left { animation: avaLeft 0.8s cubic-bezier(0.34, 1.4, 0.64, 1) 0.15s both; }
.ava-right { animation: avaRight 0.8s cubic-bezier(0.34, 1.4, 0.64, 1) 0.15s both; }
@keyframes avaLeft { from { opacity: 0; transform: translateX(-300px) rotate(-14deg); } to { opacity: 1; transform: translateX(-84px) rotate(-9deg); } }
@keyframes avaRight { from { opacity: 0; transform: translateX(300px) rotate(14deg); } to { opacity: 1; transform: translateX(84px) rotate(9deg); } }

.match-sub {
  font-family: 'Roboto Mono', monospace; font-size: 0.9em; letter-spacing: 0.03em; max-width: 640px;
  text-align: center; line-height: 1.5; color: rgba(255, 255, 255, 0.94);
  animation: matchUp 0.5s ease 0.85s both;
}
@keyframes matchUp { from { opacity: 0; transform: translateY(14px); } to { opacity: 1; transform: none; } }
</style>
