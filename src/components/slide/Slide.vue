<template>
  <Carousel :settings="settings" :breakpoints="breakpoints">
    <Slide v-for="slide in 10" :key="slide">
      <div class="carousel__item">{{ slide }}</div>
    </Slide>

    <template #addons>
      <Pagination />
    </template>
  </Carousel>
</template>

<script>
import { defineComponent } from "vue";
import { Carousel, Slide, Pagination } from "vue3-carousel";

import "vue3-carousel/dist/carousel.css";

export default defineComponent({
  name: "Breakpoints",
  components: {
    Carousel,
    Slide,
    Pagination,
  },
  data: () => ({
    // carousel settings
    settings: {
      itemsToShow: 1,
      snapAlign: "center",
    },
    // breakpoints are mobile first
    // any settings not specified will fallback to the carousel settings
    breakpoints: {
      // 700px and up
      700: {
        itemsToShow: 3.5,
        snapAlign: "center",
      },
      // 1024 and up
      1024: {
        itemsToShow: 5,
        snapAlign: "start",
      },
    },
  }),
});
</script>

<style scoped>
::v-deep * {
  box-sizing: border-box;
}
::v-deep .carousel__pagination-button {
  width: 6px;
  height: 6px;

  padding: 0;
  margin: 0;

  background-color: var(--colorGray200);
}

::v-deep .carousel__pagination-button--active {
  width: 8px;
  height: 8px;
  background-color: var(--colorPrimary200);
}

::v-deep .carousel__pagination {
  padding: 0;
  height: min-content;
}

::v-deep .carousel__pagination-item {
  height: 8px;
  width: 8px;
  width: min-content;
  display: flex;
  justify-content: center;
  align-items: center;
}
::v-deep .carousel__pagination {
  display: flex;
  gap: 8px;
  margin: 24px 0;
}
</style>
