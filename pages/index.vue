<template>
  <div>
    <v-row justify="center" align="center">
      <v-col>
        <RegisterChart />
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <SalesChart />
      </v-col>
    </v-row>
  </div>
</template>

<script>
import SalesChart from "../components/SalesChart.vue";
import RegisterChart from "../components/RegisterChart.vue";
export default {
  name: "IndexPage",
  components: { SalesChart, RegisterChart },
};
</script>
