<template>
  <q-layout view="hHh lpR fFf" class="bg-grey-1 q-mb-xl">
    <app-header @toggle-drawer="toggleLeftDrawer"></app-header>
    <app-drawer :open-drawer="leftDrawerOpen" />
    <q-page-container>
      <card-list />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref, defineAsyncComponent } from "vue";

const AppHeader = defineAsyncComponent(() =>
  import("../components/AppHeader.vue")
);
const AppDrawer = defineAsyncComponent(() =>
  import("../components/AppDrawer.vue")
);
const CardList = defineAsyncComponent(() =>
  import("../components/CardList.vue")
);

defineOptions({
  name: "IndexPage",
});

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
