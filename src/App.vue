<script>
import { reactive } from "vue";
import json from "@/data/graduates.json";
import CardComponent from "./components/CardComponent.vue";
export default {
  name: "GridSectionApp",
  components: {
    CardComponent,
  },
  setup() {
    const graduates = reactive(json);
    return { graduates };
  },
};
</script>

<template>
  <div class="testimonials">
    <card-component
      v-for="graduate in graduates"
      :key="graduate"
      :graduate="graduate"
      :class="[
        `theme-${graduate.theme}`,
        graduate.quotation ? 'quotation' : '',
        `grid-${graduate.col}-col`,
        `grid-${graduate.row}-row`,
        `order-${graduate.order}`,
      ]"
    />
  </div>
</template>

<style lang="scss">
@import "@/assets/styles/app.scss";
</style>
