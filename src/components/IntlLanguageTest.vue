<template>
  <v-card>
    <v-toolbar color="deep-purple-accent-4">
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Page test intl</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon="mdi-magnify"></v-btn>

      <v-btn icon="mdi-dots-vertical"></v-btn>

      <template v-slot:extension>
        <v-tabs v-model="currentItem" fixed-tabs>
          <v-tab
            v-for="item in items"
            :key="item"
            :text="item"
            :value="'tab-' + item"
          ></v-tab>

          <v-menu v-if="more.length">
            <template v-slot:activator="{ props }">
              <v-btn
                class="align-self-center me-4"
                height="100%"
                rounded="0"
                variant="plain"
                v-bind="props"
              >
                more

                <v-icon icon="mdi-menu-down" end></v-icon>
              </v-btn>
            </template>

            <v-list class="bg-grey-lighten-3">
              <v-list-item
                v-for="item in more"
                :key="item"
                :title="getLanguageName(item)"
              ></v-list-item>
            </v-list>
          </v-menu>
        </v-tabs>
      </template>
    </v-toolbar>

    <v-tabs-window v-model="currentItem">
      <v-tabs-window-item
        v-for="item in items.concat(more)"
        :key="item"
        :value="'tab-' + item"
      >
        <v-card flat>
          <v-card-text>
            <h2>{{ item }}</h2>
            {{ text }}
          </v-card-text>
        </v-card>
      </v-tabs-window-item>
    </v-tabs-window>
  </v-card>
</template>

<script setup>
defineProps({});

const currentItem = ref("tab-Web");
const items = ["Web", "Shopping", "Videos", "Images"];
const more = ["en", "fr", "ar", "zh", "nl"];
const text =
  "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.";

const getLanguageName = (code) => {
  const nameGenerator = new Intl.DisplayNames(code, {
    type: "language",
  });
  const displayName = nameGenerator.of(code);
  return displayName;
};
</script>
