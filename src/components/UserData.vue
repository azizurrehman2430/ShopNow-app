<template>
    <v-app>
      <v-main class="mt-1">
        <div class="mt-1">
          <div>
  
            <div class="text-right pa-4">
              <v-btn @click="dialogAddUser = true" color="blue">
                Add New User
                <v-icon icon="mdi-account" class="ml-3"></v-icon>
              </v-btn>
  
              <v-dialog v-model="dialogAddUser" transition="dialog-top-transition" max-width="600">
                <v-card title="Add New User Details">
                  <template v-slot:text>
                    <div>
                      <div class="text-subtitle-1 text-medium-emphasis">Name</div>
                      <v-text-field density="compact" placeholder="Enter Name" prepend-inner-icon="mdi-account"
                        v-model="userData.name" variant="outlined" color="blue" :rules="dataValidationRules.name"
                        required></v-text-field>
  
                      <div class="text-subtitle-1 text-medium-emphasis">Account</div>
                      <v-text-field density="compact" placeholder="Email address" prepend-inner-icon="mdi-email-outline"
                        variant="outlined" v-model="userData.email" color="blue" :rules="dataValidationRules.email"
                        required></v-text-field>
  
                      <div class="text-subtitle-1 text-medium-emphasis d-flex align-center justify-space-between">
                        Password
                      </div>
                      <v-text-field :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
                        :type="visible ? 'text' : 'password'" density="compact" placeholder="Enter your password"
                        prepend-inner-icon="mdi-lock-outline" variant="outlined" color="blue" v-model="userData.password"
                        @click:append-inner="visible = !visible" required></v-text-field>
  
                      <div class="text-subtitle-1 text-medium-emphasis">Address</div>
                      <v-text-field density="compact" placeholder="Enter Address" prepend-inner-icon="mdi-home"
                        v-model="userData.address" variant="outlined" :rules="dataValidationRules.address"
                        color="blue" required></v-text-field>
                    </div>
                  </template>
  
                  <template v-slot:actions>
                    <v-btn class="ms-auto " color="red" text="Close" @click="dialogAddUser = false">Close
                      <v-icon icon="mdi-minus-circle" end></v-icon></v-btn>
                    <v-spacer></v-spacer>
                    <v-btn class="ms-auto" color="primary " text="Add" @click="logUserData()">Add
                      <v-icon icon="mdi-checkbox-marked-circle" end></v-icon>
                    </v-btn>
                  </template>
                </v-card>
              </v-dialog>
            </div>
          </div>
  
          <v-table class="custom-table">
            <thead>
              <tr>
                <th class="text-left">Sr No</th>
                <th class="text-left">Name</th>
                <th class="text-left">Email</th>
                <th class="text-left">Password</th>
                <th class="text-left">Address</th>
                <!-- <th class="text-left">Age</th> -->
                <th class="text-left">Delete</th>
                <th class="text-left">Edit user</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(item, index) in itemArray" :key="index">
                <td>{{ index + 1 }}</td>
                <td>{{ item.name }}</td>
                <td>{{ item.email }}</td>
                <td>{{ item.password }}</td>
                <td>{{ item.address }}</td>
                <td>{{ item.age }}</td>
                <td>
                  <!-- <v-btn @click="confirmDelete(index)" color="red">Delete</v-btn> -->
                  <div class=" pa-4">
                    <v-btn @click="delDialog(item.name, index)" color="blue">
                      Delete
                      <v-icon icon="mdi-delete" class="ml-3"></v-icon>
                    </v-btn>
  
                    <v-dialog v-model="deleteDialog" transition="dialog-top-transition" max-width="600">
                      <v-card title="Delete User">
                        <template v-slot:text>
                          <span>
                            <h3>
                              Are you sure you want to delete the <span style="color:red">{{ deletedUser }}</span> ?
                            </h3>
                          </span>
                        </template>
  
                        <template v-slot:actions>
                          <v-btn class="ms-auto" color="red" text="Close" @click="deleteDialog = false">
                            close<v-icon icon="mdi-minus-circle" class="ml-3"></v-icon>
  
                          </v-btn>
                          <v-spacer></v-spacer>
                          <v-btn class="ms-auto" color="primary " text="Delete" @click="confirmDelete(index)">Delete                
                                <v-icon icon="mdi-delete" class="ml-3"></v-icon>
  
                          </v-btn>
                        </template>
                      </v-card>
                    </v-dialog>
                  </div>
                </td>
                <td>
                  <v-btn @click="editUser(index)" color="green">Edit user
                    <v-icon icon="mdi-pencil" class="ml-3"></v-icon>
                  </v-btn>
                </td>
              </tr>
            </tbody>
          </v-table>
  
          <v-dialog v-model="dialogEditUser" transition="dialog-top-transition" max-width="600">
            <v-card title="Edit User">
              <template v-slot:text>
                <div>
                  <div class="text-subtitle-1 text-medium-emphasis">Name</div>
                  <v-text-field density="compact" placeholder="Enter Name" prepend-inner-icon="mdi-account"
                    v-model="editedUserData.name"  variant="outlined" color="green" :rules="dataValidationRules.name"
                    required></v-text-field>
  
                  <div class="text-subtitle-1 text-medium-emphasis">Account</div>
                  <v-text-field density="compact" placeholder="Email address" prepend-inner-icon="mdi-email-outline"
                    variant="outlined" color="green" v-model="editedUserData.email" :rules="dataValidationRules.email" required
                    disabled></v-text-field>
  
                  <div class="text-subtitle-1 text-medium-emphasis d-flex align-center justify-space-between">
                    Password
                  </div>
                  <v-text-field :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
                    :type="visible ? 'text' : 'password'" density="compact" placeholder="Enter your password"
                    prepend-inner-icon="mdi-lock-outline" variant="outlined" color="green" v-model="editedUserData.password"
                    @click:append-inner="visible = !visible"></v-text-field>
  
                  <div class="text-subtitle-1 text-medium-emphasis">Address</div>
                  <v-text-field density="compact" placeholder="Enter Address" prepend-inner-icon="mdi-home"
                    v-model="editedUserData.address" variant="outlined"  :rules="dataValidationRules.address"
                    color="green"></v-text-field>
                </div>
              </template>
              <template v-slot:actions>
                <v-btn class="ms-auto" color="red" text="Close" @click="dialogEditUser = false">cancel
                  <v-icon icon="mdi-minus-circle" end></v-icon>
                </v-btn>
                <v-spacer></v-spacer>
                <div>
                  <v-btn class="ms-auto" color="primary" text="Save" @click="saveEditedUserData()">update                   
                     <v-icon icon="mdi-checkbox-marked-circle" end></v-icon>
  
                  </v-btn>
  
                </div>
              </template>
            </v-card>
          </v-dialog>
        </div>
        <div class="text-right mt-6 mr-5">
          <v-btn id="clear" color="red" @click="clearStorage()">delete all
            <v-icon icon="mdi-delete" class="ml-3"></v-icon>
  
          </v-btn>
        </div>
      </v-main>
    </v-app>
  </template>
  
  <script>
  export default {
    name: 'UserData',
    data() {
      return {
        dialogAddUser: false,
        dialogEditUser: false,
        deleteDialog: false,
        deletedUser: '',
        userData: {
          name: '',
          email: '',
          address: '',
          password: '',
          age: 0
        },
        editedUserData: {
          name: '',
          email: '',
          password: '',
          age: '',
          address: '',
        },
        deluserIndex: 0,
        itemArray: [],
        dataValidationRules: {
          name: [
            value => !!value || 'You must enter a Name.'
          ],
          email: [
            value => /^[a-z.-]+@[a-z.-]+\.[a-z]+$/.test(value) || 'Must be a valid e-mail.'
          ],
          address: [
            value => value && value.length > 10 || 'Address must be at least 10 characters.'
          ]
        }
      };
    },
    beforeMount() {
      this.fetchData();
    },
    methods: {
      fetchData() {
        const storedItems = JSON.parse(localStorage.getItem('itemsJson')) || [];
        this.itemArray = storedItems;
      },
      update() {
        if (localStorage.getItem('itemsJson') == null) {
          this.itemsArray = []
          localStorage.setItem('itemsJson', JSON.stringify(this.itemsArray))
        }
        else {
          this.newitemsinArray = localStorage.getItem('itemsJson')
          this.itemsArray = JSON.parse(this.newitemsinArray);
        }
      },
      logUserData() {
        this.itemArray.push({
          name: this.userData.name,
          email: this.userData.email,
          address: this.userData.address,
          password: this.userData.password,
          age: this.userData.age
        });
        localStorage.setItem('itemsJson', JSON.stringify(this.itemArray));
        this.clearForm();
        this.dialogAddUser = false;
      },
      confirmDelete() {
        this.deleteItem(this.deluserIndex);
        this.deleteDialog = false;
      },
      deleteItem(index) {
        this.itemArray.splice(index, 1);
        localStorage.setItem('itemsJson', JSON.stringify(this.itemArray));
      },
      editUser(index) {
        this.editedUserData = { ...this.itemArray[index] };
        this.dialogEditUser = true;
      },
      saveEditedUserData() {
        // Find the index of edited user in itemArray
        const index = this.itemArray.findIndex(item => item.email === this.editedUserData.email);
        if (index !== -1) {
          // Update user data
          this.itemArray.splice(index, 1, { ...this.editedUserData });
          localStorage.setItem('itemsJson', JSON.stringify(this.itemArray));
          this.dialogEditUser = false;
        }
      },
      clearStorage() {
        if (confirm("Do you really Want to clear the all data")) {
          localStorage.clear();
          this.itemArray = [];
        }
      },
      clearForm() {
        this.userData.name = '';
        this.userData.address = '';
        this.userData.email = '';
        this.userData.password = '';
        this.userData.age = 0;
      },
      delDialog(deluserName, index) {
        this.deletedUser = deluserName;
        this.deleteDialog = true;
        this.deluserIndex = index;
      }
    }
  };
  </script>
  
  <style scoped>
  .custom-table {
    border-collapse: collapse;
    width: 100%;
    position: relative;
  }
  
  .custom-table th,
  .custom-table td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: left;
  }
  
  .custom-table th {
    background-color: #f2f2f2;
    font-weight: bold;
  }
  
  .custom-table tr:nth-child(even) {
    background-color: #f2f2f2;
  }
  
  tr:hover {
    background-color: lightyellow;
  }
  
  .custom-table::before,
  .custom-table::after {
    content: "";
    position: absolute;
    top: 0;
    bottom: 0;
    width: 3px;
    background-color: #ddd;
  }
  
  .custom-table::before {
    left: 0;
  }
  
  .custom-table::after {
    right: 0;
  }
  </style>
  