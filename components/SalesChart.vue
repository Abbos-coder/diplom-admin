<template>
  <div>
    <p class="text-center text-h4 mb-12 mt-16">Продажa</p>
    <v-card class="mt-4 mx-auto" max-width="900">
      <v-sheet
        class="v-sheet--offset mx-auto"
        color="green"
        elevation="12"
        max-width="calc(100% - 32px)"
      >
        <v-sparkline
          :labels="labels"
          :value="value"
          color="white"
          line-width="2"
          padding="16"
          auto-draw
        ></v-sparkline>
      </v-sheet>

      <v-card-text class="pt-0">
        <div class="text-h6 font-weight-light mb-2">
          Продажи за последние 24 часа
        </div>
        <div class="subheading font-weight-light grey--text">
          Эффективность последней кампании
        </div>
        <v-divider class="my-2"></v-divider>
        <v-icon class="mr-2" small> mdi-clock </v-icon>
        <span class="text-caption grey--text font-weight-light">
          последняя Продажa 45 минут назад
        </span>
      </v-card-text>
    </v-card>
  </div>
</template>
<script>
export default {
  data: () => ({
    labels: ["$10", "$75", "$250", "$780", "$850", "$900", "$375", "$540"],
    value: [200, 675, 410, 390, 310, 460, 250, 240],
  }),
};
</script>
<style>
.v-sheet--offset {
  top: -24px;
  position: relative;
}
</style>
