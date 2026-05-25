<template>
  <v-container class="py-10">

    <!-- TITLE -->
    <div class="text-center mb-8">

      <h1 class="text-h3 font-weight-bold text-primary">
        Contacts App
      </h1>

      <p class="text-grey">
        Manage your contacts easily
      </p>

    </div>


    <!-- MAIN CARD -->
    <v-card
      elevation="10"
      rounded="xl"
    >

      <!-- TOOLBAR -->
      <v-toolbar
        color="primary"
        dark
      >

        <v-toolbar-title>
          My Contacts
        </v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn
          color="white"
          variant="flat"
          @click="openCreateDialog"
        >
          + Add Contact
        </v-btn>

      </v-toolbar>


      <!-- DATA TABLE -->
      <v-data-table
        :headers="headers"
        :items="contacts"
      >

        <!-- NAME -->
        <template v-slot:item.name="{ item }">

          <div class="d-flex align-center">

            <v-avatar
              color="primary"
              class="mr-3"
            >
              {{ item.name.charAt(0) }}
            </v-avatar>

            <span class="font-weight-medium">
              {{ item.name }}
            </span>

          </div>

        </template>


        <!-- EMAIL -->
        <template v-slot:item.email="{ item }">

          <div class="d-flex align-center">

            <v-icon
              color="blue"
              class="mr-2"
            >
              mdi-email
            </v-icon>

            <span>
              {{ item.email }}
            </span>

          </div>

        </template>


        <!-- PHONE -->
        <template v-slot:item.phone="{ item }">

          <div class="d-flex align-center">

            <v-icon
              color="green"
              class="mr-2"
            >
              mdi-phone
            </v-icon>

            <span>
              {{ item.phone }}
            </span>

          </div>

        </template>


        <!-- AGE -->
        <template v-slot:item.age="{ item }">

          <v-chip color="orange">
            {{ item.age }} yrs old
          </v-chip>

        </template>


        <!-- ADDRESS -->
        <template v-slot:item.address="{ item }">

          <div>

            <div>
              {{ item.address.street }}
            </div>

            <small class="text-grey">
              {{ item.address.city }},
              {{ item.address.state }}
            </small>

            <!-- ZIP CODE -->
            <div class="text-primary">
              ZIP: {{ item.address.zip }}
            </div>

          </div>

        </template>


        <!-- ACTIONS -->
        <template v-slot:item.actions="{ item }">

          <v-btn
            icon
            color="blue"
            variant="text"
            @click="openEditDialog(item)"
          >
            <v-icon>
              mdi-pencil
            </v-icon>
          </v-btn>


          <v-btn
            icon
            color="red"
            variant="text"
            @click="deleteContact(item.id)"
          >
            <v-icon>
              mdi-delete
            </v-icon>
          </v-btn>

        </template>

      </v-data-table>

    </v-card>



    <!-- CREATE DIALOG -->
    <v-dialog
      v-model="dialog"
      width="500"
    >

      <v-card rounded="xl">

        <v-toolbar
          color="primary"
          dark
        >

          <v-toolbar-title>
            Create Contact
          </v-toolbar-title>

        </v-toolbar>


        <v-card-text class="pt-5">

          <v-text-field
            label="ID"
            prepend-inner-icon="mdi-identifier"
            variant="outlined"
            v-model="id"
          ></v-text-field>


          <v-text-field
            label="Full Name"
            prepend-inner-icon="mdi-account"
            variant="outlined"
            v-model="name"
          ></v-text-field>


          <v-text-field
            label="Email"
            prepend-inner-icon="mdi-email"
            variant="outlined"
            v-model="email"
          ></v-text-field>


          <v-text-field
            label="Phone"
            prepend-inner-icon="mdi-phone"
            variant="outlined"
            v-model="phone"
          ></v-text-field>


          <v-text-field
            label="Street"
            prepend-inner-icon="mdi-home"
            variant="outlined"
            v-model="street"
          ></v-text-field>


          <v-text-field
            label="City"
            prepend-inner-icon="mdi-city"
            variant="outlined"
            v-model="city"
          ></v-text-field>


          <v-text-field
            label="State"
            prepend-inner-icon="mdi-map"
            variant="outlined"
            v-model="state"
          ></v-text-field>


          <v-text-field
            label="Zip Code"
            prepend-inner-icon="mdi-mailbox"
            variant="outlined"
            v-model="zip"
          ></v-text-field>


          <v-text-field
            label="Age"
            prepend-inner-icon="mdi-cake-variant"
            variant="outlined"
            type="number"
            v-model="age"
          ></v-text-field>

        </v-card-text>


        <v-card-actions class="pa-5">

          <v-spacer></v-spacer>

          <v-btn
            variant="text"
            @click="dialog = false"
          >
            Cancel
          </v-btn>


          <v-btn
            color="primary"
            @click="createContact"
          >
            Save
          </v-btn>

        </v-card-actions>

      </v-card>

    </v-dialog>



    <!-- UPDATE DIALOG -->
    <v-dialog
      v-model="updateDialog"
      width="500"
    >

      <v-card rounded="xl">

        <v-toolbar
          color="blue"
          dark
        >

          <v-toolbar-title>
            Update Contact
          </v-toolbar-title>

        </v-toolbar>


        <v-card-text class="pt-5">

          <v-text-field
            label="ID"
            variant="outlined"
            v-model="id"
          ></v-text-field>


          <v-text-field
            label="Full Name"
            variant="outlined"
            v-model="name"
          ></v-text-field>


          <v-text-field
            label="Email"
            variant="outlined"
            v-model="email"
          ></v-text-field>


          <v-text-field
            label="Phone"
            variant="outlined"
            v-model="phone"
          ></v-text-field>


          <v-text-field
            label="Street"
            variant="outlined"
            v-model="street"
          ></v-text-field>


          <v-text-field
            label="City"
            variant="outlined"
            v-model="city"
          ></v-text-field>


          <v-text-field
            label="State"
            variant="outlined"
            v-model="state"
          ></v-text-field>


          <v-text-field
            label="Zip"
            variant="outlined"
            v-model="zip"
          ></v-text-field>


          <v-text-field
            label="Age"
            variant="outlined"
            type="number"
            v-model="age"
          ></v-text-field>

        </v-card-text>


        <v-card-actions class="pa-5">

          <v-spacer></v-spacer>

          <v-btn
            variant="text"
            @click="updateDialog = false"
          >
            Cancel
          </v-btn>


          <v-btn
            color="blue"
            @click="updateContact"
          >
            Update
          </v-btn>

        </v-card-actions>

      </v-card>

    </v-dialog>

  </v-container>
</template>

<script setup>

// TABLE HEADERS
const headers = [
  { title: 'Name', key: 'name' },
  { title: 'Email', key: 'email' },
  { title: 'Phone', key: 'phone' },
  { title: 'Address', key: 'address' },
  { title: 'Age', key: 'age' },
  { title: 'Actions', key: 'actions' }
]


// DATA
const contacts = ref([])

const dialog = ref(false)
const updateDialog = ref(false)

const id = ref("")

const name = ref("")
const email = ref("")
const phone = ref("")

const street = ref("")
const city = ref("")
const state = ref("")
const zip = ref("")

const age = ref(0)


// API URL
const API_URL = 'https://playground.mockoon.com/contacts'


// GET CONTACTS
const getContacts = async () => {

  try {

    const data = await $fetch(API_URL)

    contacts.value = data

  } catch (err) {

    console.error(err)

  }

}


// RESET FORM
const resetForm = () => {

  id.value = ""

  name.value = ""
  email.value = ""
  phone.value = ""

  street.value = ""
  city.value = ""
  state.value = ""
  zip.value = ""

  age.value = 0

}


// OPEN CREATE
const openCreateDialog = () => {

  resetForm()

  dialog.value = true

}


// CREATE CONTACT
const createContact = async () => {

  try {

    const data = await $fetch(API_URL, {

      method: 'POST',

      body: {

        id: id.value,

        name: name.value,
        email: email.value,
        phone: phone.value,

        address: {
          street: street.value,
          city: city.value,
          state: state.value,
          zip: zip.value
        },

        age: age.value

      }

    })

    contacts.value.push(data)

    dialog.value = false

    resetForm()

  } catch (err) {

    console.error(err)

  }

}


// OPEN UPDATE
const openEditDialog = (item) => {

  id.value = item.id

  name.value = item.name
  email.value = item.email
  phone.value = item.phone

  street.value = item.address.street
  city.value = item.address.city
  state.value = item.address.state
  zip.value = item.address.zip

  age.value = item.age

  updateDialog.value = true

}


// UPDATE CONTACT
const updateContact = async () => {

  try {

    const data = await $fetch(
      `${API_URL}/${id.value}`,
      {

        method: 'PUT',

        body: {

          id: id.value,

          name: name.value,
          email: email.value,
          phone: phone.value,

          address: {
            street: street.value,
            city: city.value,
            state: state.value,
            zip: zip.value
          },

          age: age.value

        }

      }
    )

    const index = contacts.value.findIndex(
      contact => contact.id === id.value
    )

    if (index !== -1) {

      contacts.value[index] = data

    }

    updateDialog.value = false

    resetForm()

  } catch (err) {

    console.error(err)

  }

}


// DELETE CONTACT
const deleteContact = async (contactId) => {

  try {

    await $fetch(
      `${API_URL}/${contactId}`,
      {
        method: 'DELETE'
      }
    )

    contacts.value = contacts.value.filter(
      contact => contact.id !== contactId
    )

  } catch (err) {

    console.error(err)

  }

}


// ON MOUNT
onMounted(() => {

  getContacts()

})

</script>

<style scoped>

.text-grey {
  color: gray;
}

</style>