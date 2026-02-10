<template>
  <div>
    <v-row>
      <v-col cols="12" md="3">
        <v-card height="120" color="#EEEEEE">
          <v-card-text>
            <v-row>
              <v-col>
                <v-progress-circular
                  model-value="20"
                  :size="90"
                  :width="11"
                  color="blue"
                  >20%</v-progress-circular
                >
              </v-col>

              <v-col>
                <v-row no-gutters>
                  <v-col cols="12" class="text-right text-h6">Student</v-col>
                  <v-col cols="12" class="text-right text-h3">120</v-col>
                </v-row>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>

      <v-col cols="12" md="3">
        <v-card height="120" color="#EEEEEE">
          <v-card-text>
            <v-row>
              <v-col>
                <v-progress-circular
                  model-value="20"
                  :size="90"
                  :width="11"
                  color="orange"
                  >20%</v-progress-circular
                >
              </v-col>

              <v-col>
                <v-row no-gutters>
                  <v-col cols="12" class="text-right text-h6">Account</v-col>
                  <v-col cols="12" class="text-right text-h3">234</v-col>
                </v-row>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>

      <v-col cols="12" md="3">
        <v-card height="120" color="#EEEEEE">
          <v-card-text>
            <v-row>
              <v-col>
                <v-progress-circular
                  model-value="20"
                  :size="90"
                  :width="11"
                  color="red"
                  >20%</v-progress-circular
                >
              </v-col>

              <v-col>
                <v-row no-gutters>
                  <v-col cols="12" class="text-right text-h6">Expenses</v-col>
                  <v-col cols="12" class="text-right text-h3">62</v-col>
                </v-row>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>

      <v-col cols="12" md="3">
        <v-card height="120" color="#EEEEEE">
          <v-card-text>
            <v-row>
              <v-col>
                <v-progress-circular
                  model-value="20"
                  :size="90"
                  :width="11"
                  color="black"
                  >20%</v-progress-circular
                >
              </v-col>

              <v-col>
                <v-row no-gutters>
                  <v-col cols="12" class="text-right text-h6"
                    >New Employees</v-col
                  >
                  <v-col cols="12" class="text-right text-h3">34</v-col>
                </v-row>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="12" md="8">
        <v-card height="400" color="#EEEEEE">
          <v-table density="compact">
            <thead>
              <tr>
                <th class="text-left">Name</th>
                <th class="text-left">Calories</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in desserts" :key="item.name">
                <td>{{ item.name }}</td>
                <td>{{ item.calories }}</td>
              </tr>
            </tbody>
          </v-table>
        </v-card>
      </v-col>
      <v-col cols="4">
        <v-col cols="12" md="12">
         
              <v-card color="#385F73">
                <v-card-title class="text-h5">
                  Unlimited music now
                </v-card-title>

                <v-card-subtitle>
                  Listen to your favorite artists and albums whenever and
                  wherever, online and offline.
                </v-card-subtitle>

                <v-card-actions>
                  <v-btn text="Listen Now" variant="text"></v-btn>
                </v-card-actions>
              </v-card>
   
        </v-col>
        <v-col cols="12" md="12">
          <v-card height="115" color="#EEEEEE"></v-card>
        </v-col>
        <v-col cols="12" md="12">
          <v-card height="115" color="#EEEEEE"></v-card>
        </v-col>
      </v-col>
    </v-row>
  </div>
</template>

<script setup>
import { ref } from "vue";

const desserts = ref([
  {
    name: "Frozen Yogurt",
    calories: 159,
  },
  {
    name: "Ice cream sandwich",
    calories: 237,
  },
  {
    name: "Eclair",
    calories: 262,
  },
  {
    name: "Cupcake",
    calories: 305,
  },
  {
    name: "Gingerbread",
    calories: 356,
  },
  {
    name: "Jelly bean",
    calories: 375,
  },
  {
    name: "Lollipop",
    calories: 392,
  },
  {
    name: "Honeycomb",
    calories: 408,
  },
  {
    name: "Donut",
    calories: 452,
  },
  {
    name: "KitKat",
    calories: 518,
  },
]);
</script>

<style>
</style>