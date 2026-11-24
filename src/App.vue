<script setup lang="ts">
import { onMounted } from 'vue'
import { storeToRefs } from 'pinia'
import { RouterLink, RouterView } from 'vue-router'
import { useDeliveryStore } from './store'
const store = useDeliveryStore()
const { approvedShare, offers, urgent } = storeToRefs(store)
onMounted(store.load)
</script>

<template><div class="shell"><aside><div class="brand">HumanCapitalEU<span>OBSERVATORY</span></div><nav><RouterLink to="/">Policy evidence files</RouterLink><RouterLink to="/insights">Evidence guidance</RouterLink></nav><div class="health"><i /> Java evidence service connected</div></aside><main><header><div><span class="eyebrow">Connect workforce evidence to policy choices on skills, education, participation and job quality</span><h1>Human Capital Policy Observatory Room</h1></div><button @click="store.addOffer">Add policy evidence file</button></header><section class="summary"><article><small>Evidence approved</small><strong>{{ approvedShare }}%</strong><div class="bar"><span :style="{ width: `${approvedShare}%` }" /></div></article><article><small>Policy files</small><strong>{{ offers.length }}</strong><p>Shared observatory view</p></article><article><small>Priority skills gaps</small><strong>{{ urgent }}</strong><p>Needs attention</p></article></section><RouterView /></main></div></template>
