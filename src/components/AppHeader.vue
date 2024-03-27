<template>
  <q-header class="bg-white text-grey-8 q-py-xs" height-hint="58">
    <q-toolbar>
      <q-btn
        flat
        dense
        round
        @click="handleDrawerToggle"
        aria-label="Menu"
        icon="menu"
      />

      <q-btn flat no-caps no-wrap class="q-ml-xs" v-if="$q.screen.gt.xs">
        <q-icon :name="fabYoutube" color="red" size="28px" />
        <q-toolbar-title shrink class="text-weight-bold">
          YouTube
        </q-toolbar-title>
      </q-btn>

      <q-space />
      <div class="YL__toolbar-input-container row no-wrap">
        <q-input
          dense
          outlined
          rounded
          v-model="search"
          placeholder="Search"
          class="bg-white col"
        >
          <template v-slot:append>
            <q-btn
              unelevated
              dense
              icon="keyboard_alt"
              v-if="$q.screen.gt.sm"
            />
            <q-btn
              unelevated
              rounded
              color="grey-3"
              icon="search"
              class="text-grey-8"
            />
          </template>
        </q-input>
        <div class="flex items-center" v-if="$q.screen.gt.sm">
          <q-icon name="mic" size="28px" />
        </div>
      </div>

      <q-space />

      <div class="q-gutter-sm row items-center no-wrap">
        <q-btn
          round
          dense
          flat
          color="grey-8"
          icon="more_vert"
          v-if="$q.screen.gt.sm"
        >
          <q-tooltip>Options</q-tooltip>
        </q-btn>
        <q-btn round flat>
          <q-btn
            color="primary"
            rounded
            outline
            icon="account_circle"
            :label="$q.screen.gt.sm ? 'My Account' : ''"
          />
          <q-tooltip>Account</q-tooltip>
        </q-btn>
        <q-btn
          round
          dense
          flat
          color="grey-9"
          icon="invert_colors"
          v-if="$q.screen.gt.sm"
        >
          <q-tooltip>Invert Color</q-tooltip>
        </q-btn>
      </div>
    </q-toolbar>
  </q-header>
</template>

<script setup>
import { ref } from "vue";
import { fabYoutube } from "@quasar/extras/fontawesome-v6";

defineOptions({
  name: "AppHeader",
});
const search = ref("");

const handleDrawerToggle = () => emit("toggle-drawer");

const emit = defineEmits(["toggle-drawer"]);
</script>

<style lang="scss">
.YL {
  &__toolbar-input-container {
    min-width: 100px;
    width: 55%;
  }

  &__toolbar-input-btn {
    border-radius: 0;
    border-style: solid;
    border-width: 1px 1px 1px 0;
    border-color: rgba(0, 0, 0, 0.24);
    max-width: 60px;
    width: 100%;
  }

  &__drawer-footer-link {
    color: inherit;
    text-decoration: none;
    font-weight: 500;
    font-size: 0.75rem;
  }
  &:hover {
    color: #000;
  }
}
</style>
