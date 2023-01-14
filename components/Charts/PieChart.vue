<template>
  <Doughnut :data="data" :options="options"/>
</template>

<script lang="ts">
import { ArcElement, Chart as ChartJS, Legend, Tooltip } from 'chart.js'
import { Doughnut } from 'vue-chartjs'
import * as chartConfig from '../../chartConfig.js'

ChartJS.register(ArcElement, Tooltip, Legend)

export default {
  name: 'PieChart',
  components: {
    Doughnut
  },
  data() {
    return chartConfig
  }
}
</script>
