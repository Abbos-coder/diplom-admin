<template>
  <div>
    <p class="text-center text-h4 mb-10 mt-5">Регистрация</p>
    <v-card class="mt-4 mx-auto" max-width="900">
      <v-sheet
        class="v-sheet--offset mx-auto"
        color="cyan"
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
          Регистрация пользователей
        </div>
        <div class="subheading font-weight-light grey--text">
          Эффективность последней кампании
        </div>
        <v-divider class="my-2"></v-divider>
        <v-icon class="mr-2" small> mdi-clock </v-icon>
        <span class="text-caption grey--text font-weight-light">
          последняя регистрация 26 минут назад
        </span>
      </v-card-text>
    </v-card>
  </div>
</template>
<script>
export default {
  data: () => ({
    labels: ["12am", "3am", "6am", "9am", "12pm", "3pm", "6pm", "9pm"],
    value: [20, 75, 10, 90, 31, 60, 150, 40],
  }),
};
</script>
<style>
.v-sheet--offset {
  top: -24px;
  position: relative;
}
</style>
