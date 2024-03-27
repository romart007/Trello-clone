<template>
  <q-card class="my-card q-gutter-md">
    <q-card-section class="q-ma-none q-pa-none">
      <q-img fit :ratio="4 / 3" :src="img"></q-img>
    </q-card-section>
    <q-card-section>
      <q-item>
        <q-item-section avatar>
          <q-avatar>
            <q-img
              fit
              :src="`https://cdn.quasar.dev/img/avatar${
                id === 7 || id === 8 ? 2 : id
              }.jpg`"
            />
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label lines="1">{{ title }}</q-item-label>
          <q-item-label caption lines="2">
            <span class="text-weight-bold">{{ channelName }}</span>
          </q-item-label>
          <q-item-label lines="1">{{ channel }} times</q-item-label>
        </q-item-section>
      </q-item>
    </q-card-section>
  </q-card>
</template>
<script setup>
import { defineProps } from "vue";

defineOptions({
  name: "CardItem",
});

const props = defineProps(["id", "img", "title", "channelName", "channel"]);
</script>
