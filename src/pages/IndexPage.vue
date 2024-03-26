<template>
  <q-layout view="hHh lpR fFf" class="bg-grey-1">
    <q-header class="bg-white text-grey-8 q-py-xs" height-hint="58">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="toggleLeftDrawer"
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
              <q-btn unelevated dense icon="keyboard_alt" />
              <q-btn
                unelevated
                rounded
                color="grey-3"
                icon="search"
                class="text-grey-8"
              />
            </template>
          </q-input>
          <div class="flex items-center">
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
          <!-- <q-btn
            round
            dense
            flat
            color="grey-8"
            icon="apps"
            v-if="$q.screen.gt.sm"
          >
            <q-tooltip>Apps</q-tooltip>
          </q-btn>
          <q-btn
            round
            dense
            flat
            color="grey-8"
            icon="message"
            v-if="$q.screen.gt.sm"
          >
            <q-tooltip>Messages</q-tooltip>
          </q-btn>
          <q-btn round dense flat color="grey-8" icon="notifications">
            <q-badge color="red" text-color="white" floating> 2 </q-badge>
            <q-tooltip>Notifications</q-tooltip>
          </q-btn> -->
          <q-btn round flat>
            <q-btn
              color="primary"
              rounded
              outline
              icon="account_circle"
              label="My Account"
            />
            <q-tooltip>Account</q-tooltip>
            <!-- <q-avatar size="26px">
              <img src="https://cdn.quasar.dev/img/boy-avatar.png" />
            </q-avatar>
            <q-tooltip>Account</q-tooltip>
            <span>My Account</span> -->
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

    <q-drawer v-model="leftDrawerOpen" show-if-above class="white" :width="90">
      <q-scroll-area class="fit">
        <q-list padding>
          <q-item v-for="link in links1" :key="link.text" v-ripple clickable>
            <q-item-section avatar>
              <q-icon color="grey-8" :name="link.icon" />
              <q-item-label caption>
                <span>{{ link.text }}</span>
              </q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <!-- <router-view /> -->
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
          <q-card class="my-card q-gutter-md">
            <q-card-section class="q-ma-none q-pa-none">
              <q-img :src="vid.img"></q-img>
            </q-card-section>
            <q-card-section>
              <q-item>
                <q-item-section avatar>
                  <q-avatar>
                    <img
                      :src="`https://cdn.quasar.dev/img/avatar${
                        vid.id !== 6 ? vid.id : 1
                      }.jpg`"
                    />
                  </q-avatar>
                </q-item-section>

                <q-item-section>
                  <q-item-label lines="1">{{ vid.title }}</q-item-label>
                  <q-item-label caption lines="2">
                    <span class="text-weight-bold">{{ vid.channelName }}</span>
                  </q-item-label>
                  <q-item-label lines="1">{{ vid.channel }} times</q-item-label>
                </q-item-section>
              </q-item>
            </q-card-section>
          </q-card>
        </q-col>
      </div>
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from "vue";
import { fabYoutube } from "@quasar/extras/fontawesome-v6";

export default {
  name: "MyLayout",

  setup() {
    const leftDrawerOpen = ref(false);
    const search = ref("");

    function toggleLeftDrawer() {
      leftDrawerOpen.value = !leftDrawerOpen.value;
    }

    const videos = ref([
      {
        id: 1,
        title: "News 1",
        channelName: "News Channel 1",
        channel: 100,
        img: "https://cdn.quasar.dev/img/mountains.jpg",
      },
      {
        id: 2,
        title: "News 2",
        channelName: "News Channel 2",
        channel: 321,
        img: "https://cdn.quasar.dev/img/mountains.jpg",
      },
      {
        id: 3,
        title: "News 3",
        channelName: "News Channel 3",
        channel: 231,
        img: "https://cdn.quasar.dev/img/mountains.jpg",
      },
      {
        id: 4,
        title: "News 4",
        channelName: "News Channel 4",
        channel: 111,
        img: "https://cdn.quasar.dev/img/mountains.jpg",
      },
      {
        id: 5,
        title: "News 4",
        channelName: "News Channel 4",
        channel: 111,
        img: "https://cdn.quasar.dev/img/mountains.jpg",
      },
      {
        id: 6,
        title: "News 6",
        channelName: "News Channel 6",
        channel: 22,
        img: "https://cdn.quasar.dev/img/parallax2.jpg",
      },
      {
        id: 7,
        title: "News 7",
        channelName: "News Channel 7",
        channel: 12,
        img: "https://cdn.quasar.dev/img/parallax2.jpg",
      },
      {
        id: 8,
        title: "News 8",
        channelName: "News Channel 8",
        channel: 131,
        img: "https://cdn.quasar.dev/img/quasar.jpg",
      },
      // Add more users here as needed
    ]);

    return {
      videos,

      fabYoutube,

      leftDrawerOpen,
      search,

      toggleLeftDrawer,

      links1: [
        { icon: "home", text: "Home" },
        { icon: "music_video", text: "Shorts" },
        { icon: "ondemand_video", text: "Subscribe" },
        { icon: "video_library", text: "Library" },
        { icon: "restore", text: "History" },
      ],
      // links2: [
      //   { icon: "folder", text: "Library" },
      //   { icon: "restore", text: "History" },
      //   { icon: "watch_later", text: "Watch later" },
      //   { icon: "thumb_up_alt", text: "Liked videos" },
      // ],
      // links3: [
      //   { icon: fabYoutube, text: "YouTube Premium" },
      //   { icon: "local_movies", text: "Movies & Shows" },
      //   { icon: "videogame_asset", text: "Gaming" },
      //   { icon: "live_tv", text: "Live" },
      // ],
      // links4: [
      //   { icon: "settings", text: "Settings" },
      //   { icon: "flag", text: "Report history" },
      //   { icon: "help", text: "Help" },
      //   { icon: "feedback", text: "Send feedback" },
      // ],
      // buttons1: [
      //   { text: "About" },
      //   { text: "Press" },
      //   { text: "Copyright" },
      //   { text: "Contact us" },
      //   { text: "Creators" },
      //   { text: "Advertise" },
      //   { text: "Developers" },
      // ],
      // buttons2: [
      //   { text: "Terms" },
      //   { text: "Privacy" },
      //   { text: "Policy & Safety" },
      //   { text: "Test new features" },
      // ],
    };
  },
};
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
