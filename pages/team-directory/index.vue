<template>
  <v-card flat>
    <v-toolbar
      color="primary"
      dark
      extended
      flat
    >
      <!-- <v-toolbar-side-icon></v-toolbar-side-icon> -->
      <v-icon>person</v-icon>
      <v-toolbar-title class="white--text">Team Directory</v-toolbar-title>
    </v-toolbar>

    <v-layout row pb-2>
      <v-flex xs10 offset-xs1>
        <v-card class="card--flex-toolbar">
          <v-toolbar
            color="white"
            class="black--text"
            dark
            tabs
            flat
          >
            <v-toolbar-title>Team Directory Agency</v-toolbar-title>
            <v-spacer></v-spacer>
            <v-tabs
              slot="extension"
              v-model="tab"
              color="white"
              class="black--text"
              grow
            >
              <v-tabs-slider color="primary"></v-tabs-slider>

              <v-tab
                v-for="item in items"
                :key="item"
                class="black--text"
              >
                {{ item }}
              </v-tab>
            </v-tabs>
          </v-toolbar>

          <v-tabs-items v-model="tab">
            <v-tab-item
              v-for="item in items"
              :key="item"
            >
              <v-data-table
                :items="desserts"
                class="elevation-1"
                hide-actions
                hide-headers
              >
                <template slot="items" slot-scope="props">
                  <td class="text-xs-left">{{ props.item.name }}</td>
                  <td class="text-xs-left">{{ props.item.calories }}</td>
                  <td class="text-xs-left">{{ props.item.fat }}</td>
                  <td class="text-xs-right">{{ props.item.carbs }}</td>
                </template>
              </v-data-table>
            </v-tab-item>
          </v-tabs-items>

          <v-divider></v-divider>

          <v-card-text style="height: 200px;"></v-card-text>
        </v-card>
      </v-flex>
    </v-layout>
  </v-card>
</template>

<script>
  export default {
    data () {
      return {
        dialog: false,
        tab: null,
        items: [
          'Active(29)', 'Pending(11)', 'Deactvated(3)', 'Administartors(14)'
        ],
        desserts: [
          {
            value: false,
            name: 'priyam bhanji(admin)',
            calories: 159,
            fat: 6.0,
            carbs: 24
          },
          {
            value: false,
            name: 'kylee sfdsf',
            calories: 237,
            fat: 9.0,
            carbs: 37
          },
          {
            value: false,
            name: 'dsfsdf fsdfsdf',
            calories: 262,
            fat: 16.0,
            carbs: 23
          },
          {
            value: false,
            name: 'fsdfdsf fsdfsd',
            calories: 305,
            fat: 3.7,
            carbs: 67
          },
          {
            value: false,
            name: 'sadsadsad asfsafs',
            calories: 356,
            fat: 16.0,
            carbs: 49
          },
          {
            value: false,
            name: 'dsadas bean',
            calories: 375,
            fat: 0.0,
            carbs: 94
          },
          {
            value: false,
            name: 'dsad sadsad',
            calories: 392,
            fat: 0.2,
            carbs: 98
          },
          {
            value: false,
            name: 'sdsd dasd asd',
            calories: 408,
            fat: 3.2,
            carbs: 87
          },
          {
            value: false,
            name: 'dsads dsasad',
            calories: 452,
            fat: 25.0,
            carbs: 51
          },
          {
            value: false,
            name: 'sadsad dsadda',
            calories: 518,
            fat: 26.0,
            carbs: 65
          }
        ]
      }
    }
  }
</script>

<style>
  .card--flex-toolbar {
    margin-top: -64px;
  }
</style>