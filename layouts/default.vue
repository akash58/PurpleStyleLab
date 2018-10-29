<template>
  <v-app>
    <v-navigation-drawer
      :mini-variant.sync="miniVariant"
      :clipped="clipped"
      v-model="drawer"
      fixed
      app
    >
    <v-toolbar dense flat>
      <v-list>
        <v-list-tile>
          <v-list-tile-title class="title">
            Application
          </v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-toolbar>
    <v-divider></v-divider>
    <no-ssr>
      <v-list>
        <nuxt-link to="/" class="tdn">
          <v-list-tile @click="">
            <v-list-tile-action>
              <v-icon color="grey darken-1" size="18" class="pl-1">insert_drive_file</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title class="black--text roboto-regular">Orders</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </nuxt-link>
        <!-- <nuxt-link to="/support" class="tdn"> -->
          <v-list-tile @click="dialog = true">
            <v-list-tile-action>
              <v-icon color="grey darken-1" size="18" class="pl-1">contact_support</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title class="black--text roboto-regular">Support</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        <!-- </nuxt-link> -->
        <v-dialog
          v-model="dialog"
          max-width="320"
        >
          <v-card>
            <v-toolbar dark color="primary" flat>
              <v-toolbar-title class="subheading">We love your feedback!</v-toolbar-title>
              <v-spacer></v-spacer>
              <v-btn icon dark @click.native="close">
                <v-icon>close</v-icon>
              </v-btn>
            </v-toolbar>
            <v-card-text>
              <v-layout wrap>
                <v-flex xs12>
                  <v-select
                    :items="['I have some feedback', 'I have some suggestion']"
                    v-model="editedItem.feedback"
                    label="Topic"
                    required
                  ></v-select>
                </v-flex>
                <v-flex xs12>
                  <v-textarea
                    v-model="editedItem.name"
                    :counter="500"
                    label="Share your ideas"
                    rows="1"
                    auto-grow
                  ></v-textarea>
                </v-flex>
              </v-layout>
            </v-card-text>
            <v-divider></v-divider>
            <v-layout class="pa-3">
              Your satisfaction is very important to us. if your issue require immediate attention please contact SafeWire support team at 614-362-8058. 
            </v-layout>
            <v-divider></v-divider>
            <v-card-actions class="blue-grey lighten-5 py-4">
              <v-spacer></v-spacer>
              <v-btn
                round 
                color="blue darken-1"
                class="white--text"
                @click.native="save"
              >
                Send
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
        <v-list-group prepend-icon="person">
          <v-list-tile slot="activator">
            <v-list-tile-content>
              <v-list-tile-title class="black--text roboto-regular">Administartions</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
          <v-list-tile
            router
            :to="item.to"
            :key="i"
            v-for="(item, i) in items"
            exact
          >
            <v-list-tile-action>
              <v-icon v-html="item.icon"></v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title v-text="item.title"></v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list-group>
      </v-list>
    </no-ssr>
    </v-navigation-drawer>
    <v-toolbar fixed app :clipped-left="clipped" dense flat>
      <v-toolbar-side-icon @click="drawer = !drawer"></v-toolbar-side-icon>
      <v-spacer></v-spacer>
      <v-menu offset-y origin="center center" :nudge-bottom="10" transition="scale-transition">
        <v-btn icon large flat slot="activator">
          <v-avatar size="30px">
            <img src="avatar/man_4.jpg" alt="Michael Wang"/>
          </v-avatar>
        </v-btn>
        <v-list class="pa-0">
          <v-list-tile @click="" ripple="ripple">
            <v-list-tile-action>
              <v-icon>account_circle</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>Profile</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
          <v-list-tile @click="" ripple="ripple">
            <v-list-tile-action>
              <v-icon>settings</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>Settings</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
          <nuxt-link to="/" class="tdn black--text">
            <v-list-tile @click="" ripple="ripple">
              <v-list-tile-action>
                <v-icon>fullscreen_exit</v-icon>
              </v-list-tile-action>
              <v-list-tile-content>
                <v-list-tile-title>Logout</v-list-tile-title>
              </v-list-tile-content>
            </v-list-tile>
          </nuxt-link>
        </v-list>
      </v-menu>
    </v-toolbar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-navigation-drawer
      temporary
      :right="right"
      v-model="rightDrawer"
      fixed
    >
      <v-list>
        <v-list-tile @click.native="right = !right">
          <v-list-tile-action>
            <v-icon light>compare_arrows</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>Switch drawer (click me)</v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-footer :fixed="fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        dialog: false,
        clipped: false,
        drawer: true,
        fixed: false,
        items: [
          { icon: 'apps', title: 'Team Directory', to: '/team-directory' },
          { icon: 'bubble_chart', title: 'Escow Accounts', to: '/escrow-account' }
        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Vuetify.js',
        headers: [
          {
            text: 'Dessert (100g serving)',
            align: 'left',
            sortable: false,
            value: 'name'
          },
          { text: 'Feedbacks', value: 'feedback' }
        ],
        desserts: [],
        editedIndex: -1,
        editedItem: {
          feedback: '',
          name: ''
        },
        defaultItem: {
          feedback: '',
          name: ''
        }
      }
    },
    computed: {
      formTitle () {
        return this.editedIndex === -1 ? 'New Item' : 'Edit Item'
      }
    },

    watch: {
      dialog (val) {
        val || this.close()
      }
    },

    created () {
      this.initialize()
    },
    methods: {
      initialize () {
        this.desserts = [
          {
            feedback: 'I have some feedback',
            name: 'Frozen Yogurt'
          }
        ]
      },

      editItem (item) {
        this.editedIndex = this.desserts.indexOf(item)
        this.editedItem = Object.assign({}, item)
        this.dialog = true
      },

      deleteItem (item) {
        const index = this.desserts.indexOf(item)
        confirm('Are you sure you want to delete this item?') && this.desserts.splice(index, 1)
      },

      close () {
        this.dialog = false
        setTimeout(() => {
          this.editedItem = Object.assign({}, this.defaultItem)
          this.editedIndex = -1
        }, 300)
      },

      save () {
        if (this.editedIndex > -1) {
          Object.assign(this.desserts[this.editedIndex], this.editedItem)
        } else {
          this.desserts.push(this.editedItem)
        }
        this.close()
      }
    }
  }
</script>

<style lang="stylus" scoped>
  .tdn {
    text-decoration: none;
  }
  .pl55 {
    padding-left: 55px;
  }
  .setting-fab 
    top:50%!important; 
    right:0;
    border-radius:0  
  .page-wrapper
    min-height:calc(100vh - 64px - 50px - 81px ); 

</style>