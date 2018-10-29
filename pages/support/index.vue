<!-- <template>
	<div>
		<v-dialog v-model="dialog" max-width="320">
	    <v-btn icon slot="activator">
	      <v-icon color="grey lighten-1">feedback</v-icon>
	    </v-btn>
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
	  <v-data-table
      :items="desserts"
      hide-actions
      hide-headers
      class="elevation-1"
    >
      <template slot="items" slot-scope="props">
        <td class="" xs4>{{ props.item.feedback }}</td>
        <td class="" xs4>{{ props.item.name }}</td>
      </template>
      <template slot="no-data">
        <v-btn color="primary" @click="initialize">Reset</v-btn>
      </template>
    </v-data-table>
	</div>
</template>

<script>
  export default {
    data () {
      return {
        dialog: false,
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
        },
        tab: null,
        items: [
          'Active(29)', 'Pending(11)', 'Deactvated(3)', 'Administartors(14)'
        ],
        text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.'
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

<style>
  .card--flex-toolbar {
    margin-top: -64px;
  }
</style> -->