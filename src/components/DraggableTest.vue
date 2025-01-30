<template>
  <v-card color="grey-lighten-4" height="auto" rounded="0" flat>
    <v-toolbar color="blue-lighten-1" extended>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>DraggableTest</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-toolbar>
    <v-container>
      <v-row>
        <v-col cols="12" md="6">
          <v-card class="overflow-y-auto" elevation="10" height="500">
            <v-card-title> Liste 1 </v-card-title>
            <v-card-text>
              <draggable
                style="height: 450px"
                item-key="id"
                v-model="list"
                group="ownerPhase"
              >
                <template #item="{ element: currentElement }">
                  <v-card height="50" class="mt-5 aw-card">
                    <v-card-text>
                      {{ currentElement.name }}
                    </v-card-text>
                  </v-card>
                </template>
              </draggable>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="12" md="6">
          <v-card class="overflow-y-auto" elevation="10" height="500">
            <v-card-title> Liste 2 </v-card-title>
            <v-card-text>
              <draggable
                style="height: 450px"
                item-key="id"
                v-model="list2"
                group="ownerPhase"
              >
                <template #item="{ element: currentElement }">
                  <v-card height="50" class="mt-5 aw-card1">
                    <v-card-text>
                      <span>{{ currentElement.name }}</span>
                    </v-card-text>
                  </v-card>
                </template></draggable
              >
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script setup>
import draggable from "vuedraggable";
defineProps({});

const message = [
  "vue.draggable",
  "draggable",
  "component",
  "for",
  "vue.js 2.0",
  "based",
  "on",
  "Sortablejs",
];

var list = ref(
  message.map((name, index) => {
    return { name, order: index + 1, fixed: false };
  })
);
var list2 = ref([]);
</script>
