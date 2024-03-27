<template>
  <div
    class="cards-container row q-gutter-xl justify-center rounded-borders q-mt-xs"
  >
    <q-col
      v-for="vid in videos"
      :key="vid.id"
      cols="12"
      sm="12"
      md="6"
      lg="3"
      class="col-container"
    >
      <CardItem v-bind="vid" />
    </q-col>
  </div>
</template>
<script setup>
import { ref, defineAsyncComponent } from "vue";
import { videosList } from "../data/videos";

const CardItem = defineAsyncComponent(() => import("./CardItem.vue"));

defineOptions({
  name: "CardList",
});

const videos = ref(videosList);
</script>
<style lang="scss">
.cards-container {
  margin-top: -25px;
  .col-container {
    width: 20%;

    .q-card {
      border-radius: 5%;
    }

    .q-img__image {
      border-top-right-radius: 5%;
      border-top-left-radius: 5%;
    }
  }
}

.q-field--outlined .q-field__control {
  padding-right: 1px;
}

.q-btn {
  padding-top: 7px;
  padding-bottom: 7px;
}
</style>
