<template>
  <q-drawer v-model="isDrawerOpen" show-if-above class="white" :width="90">
    <q-scroll-area class="fit">
      <q-list padding>
        <q-item v-for="link in drawerLinks" :key="link.text" v-ripple clickable>
          <q-item-section avatar>
            <q-icon color="black" :name="link.icon" />
            <q-item-label caption>
              <span>{{ link.text }}</span>
            </q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-scroll-area>
  </q-drawer>
</template>

<script setup>
import { defineProps, watch, ref } from "vue";
import { drawerLinks } from "../data/links";

defineOptions({
  name: "AppDrawer",
});

const props = defineProps(["openDrawer"]);

const isDrawerOpen = ref(props.openDrawer);

watch(props, (newVal, _) => (isDrawerOpen.value = !newVal.openDrawer));
</script>
