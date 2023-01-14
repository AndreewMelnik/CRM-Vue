<template>
<v-container>
  <v-row>
    <v-col cols="12" sm="4">
      <BarChart/>
    </v-col>
    <v-col cols="12" sm="4">
      <PieChart/>
    </v-col>
    <v-col cols="12" sm="4">
      <LineChart/>
    </v-col>
  </v-row>
</v-container>

</template>

<script>
import BarChart from "../components/Charts/BarChart";
import PieChart from "../components/Charts/PieChart";
import LineChart from "../components/Charts/LineChart";
export default {
  name: "sales",
  components: {PieChart, BarChart, LineChart}

}
</script>

<style scoped>

</style>