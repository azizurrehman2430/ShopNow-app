<template>
    <v-app>
      <v-app-bar color="rgb(0, 123, 137)">
        <h4>Shop<span style="color:orange">Now</span></h4>
        <v-spacer></v-spacer>
        <div class="navbar">
          <v-btn to="/">Home</v-btn> |
          <v-btn to="/about">Products</v-btn> |
          <v-btn to="/contact">Contact US</v-btn> |
          <v-btn to="/Users">Users</v-btn> |
          <template>
  <div class="text-center pa-4">
    <v-btn @click="dialog = true" to="/services">
      Login
    </v-btn>

    <v-dialog
      v-model="dialog"
      width="auto"
    >
        <!-- max-width="400" -->
        <div v-if ="loginForm">
       <v-card
        class="mx-auto mt-16 pa-12 pb-8"
        elevation="8"
        max-width="448"
        rounded="lg">
      
        <div class="text-subtitle-1 text-medium-emphasis">Account</div>
  
        <v-text-field
          density="compact"
          placeholder="Email address"
          prepend-inner-icon="mdi-email-outline"
          variant="outlined"
          v-model="userData.email"
          :rules="dataValidationRules.email" required
        ></v-text-field>
  
        <div class="text-subtitle-1 text-medium-emphasis d-flex align-center justify-space-between">
          Password
  
          <a
            class="text-caption text-decoration-none text-blue"
            href="#"
            rel="noopener noreferrer"
            target="_blank"
          >
            Forgot login password?</a>
        </div>
  
        <v-text-field
          :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="visible ? 'text' : 'password'"
          density="compact"
          placeholder="Enter your password"
          prepend-inner-icon="mdi-lock-outline"
          variant="outlined"
          @click:append-inner="visible = !visible"
          :rules="dataValidationRules.password" required
          v-model="userData.password"

        ></v-text-field>
  
        <v-card
          class="mb-12"
          color="surface-variant"
          variant="tonal"
        >
          <v-card-text class="text-medium-emphasis text-caption">
            Warning: After 3 consecutive failed login attempts, you account will be temporarily locked for three hours. If you must login now, you can also click "Forgot login password?" below to reset the login password.
          </v-card-text>
        </v-card>
 
        <v-btn
          class="mb-8"
           type="submit"
          color="blue"
          size="large"
          variant="tonal"
          block 
          v-on:click="login()"
        >
          Log In
           <a href="../src/views/HomeView.vue" target="_blank"> </a> 
        </v-btn>
  
        <div>

<div class="text-right pa-4">
  <v-btn @click="dialogAddUser = true" class="Btn" color="blue">
    Sign Up
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

          <!-- <div class="text-subtitle-1 text-medium-emphasis">Age</div>
          <v-text-field density="compact" placeholder="Enter your age" v-model="userData.age"
            variant="outlined"  color="blue" required></v-text-field> -->

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
        <v-btn class="ms-auto" color="primary " text="Add" @click="logUserData()">Submit
          <v-icon icon="mdi-checkbox-marked-circle" end></v-icon>
        </v-btn>
      </template>
    </v-card>
  </v-dialog>
</div>
<!-- <tbody>
            <tr v-for="(item, index) in itemArray" :key="index">
              <td>{{ index + 1 }}</td>
              <td>{{ item.name }}</td>
              <td>{{ item.email }}</td>
              <td>{{ item.password }}</td>
              <td>{{ item.address }}</td>
            </tr>
              </tbody> -->
</div>
</v-card>
      </div>
      >
        <template v-slot:actions>
          <v-btn
            class="ms-auto"
            
            @click="dialog = false"
          ></v-btn>
        </template>
      
    </v-dialog>
  </div>
</template>
        </div>
        <v-spacer></v-spacer>
        <v-btn icon color="red">
        <v-icon>mdi-heart</v-icon>
      </v-btn>
        <v-tooltip
          v-model="show"
          location="top"
        >
        <template v-slot:activator="{ props }">
            <v-btn
              icon
              v-bind="props"
            >
              <v-icon color="green-lighten-1">
                mdi-cart
              </v-icon>
            </v-btn>
          </template>
        </v-tooltip>
        <v-menu  offset-y class="custom-menu">
            <template v-slot:activator="{ props }">
              <v-btn icon v-bind="props" class="menu-icon">
                <v-icon>mdi-account-circle</v-icon>
              </v-btn>
            </template>
          <v-list v-if="currentUser"  class="menu-list">
            <v-list-item  class="menu-list-item">
              <v-list-item-avatar>
                  <v-avatar size="40" class="avatar">
                    <v-icon   color="blue-darken-2" size="x-large" class="logo">mdi-account-circle</v-icon>
                  </v-avatar>
                </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title class="menu-title">{{ currentUser.name }}</v-list-item-title>
                <v-list-item-subtitle class="menu-subtitle">{{ currentUser.email }}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
            <v-divider></v-divider>
            <v-list-item @click="logout">
              <v-list-item-title class="logout-btn"> <v-icon color="blue-darken-2 mr-1 mb-1">mdi-logout</v-icon>Logout</v-list-item-title>
            </v-list-item>
          </v-list>
          <v-list v-else>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>No user logged in</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-menu>
      </v-app-bar>
      <router-view />
    
      <FooterSection/>
    </v-app>
  </template>
  
  <script>
  import FooterSection from '@/components/FooterSection.vue';
  export default {
    name: "HomeView",
    data() {
      return {
        currentUser: null,
        dialog: true,
          dialogAddUser: false,
      userData: {
        name: '',
        email: '',
        address: '',
        password: '',
        age: 0
      },
          userData1: {
            email: '',
            password: '',
          },
          itemArray: [],
          usersArray:[
            {
              name:"Muhammad Numan",
              email:"numanrazzaq@gmail.com",
              password:"12345678",
              phNo:"03041792624",
              address:"Chak no 24 Wb Vehari",
              login:false
            },
            {
              name:"Hamid",
              email:"hamid@gmail.com",
              password:"12345678",
              phNo:"03041792624",
              address:"Chak no 28 Wb Vehari",
              login:false
            }
          ],
          loginForm:true,
          dataValidationRules: {
            email: [
            value => {
              if (/^[a-z.-]+@[a-z.-]+\.[a-z]+$/i.test(value)) return true
              return 'Must be a valid e-mail.'
            },],
            password: [
            value => {
              if (value?.length >= 8 && /[0-9-]+/.test(value)) return true
  
              return 'Password needs to be at least 8 digits.'
            },],
          }
    }
    },
    components:{
        FooterSection
    },
    beforeMount() {
    this.fetchData();
    this.checkLoggedIn();
    this.update();
  },
    mounted() {
      this.getCurrentUser();
      this.checkLoggedIn();
    },
    methods: {
      fetchData() {
      const storedItems = JSON.parse(localStorage.getItem('itemsJson')) || [];
      this.itemArray = storedItems;
    },
    update() {
      if (localStorage.getItem('itemsJson') == null) {
        this.itemsArray = this.usersArray;
        localStorage.setItem('itemsJson', JSON.stringify(this.itemsArray))
      }
      else {
        this.newitemsinArray = localStorage.getItem('itemsJson')
        this.itemsArray = JSON.parse(this.newitemsinArray);
      }
    },
      getCurrentUser() {
        const storedItems = JSON.parse(localStorage.getItem('itemsJson'));
        const userEmail = localStorage.getItem('userEmail'); // Get the logged-in user's email from localStorage
  
        console.log("Stored items:", storedItems); // Debug log
        console.log("User email from localStorage:", userEmail); // Debug log
  
        if (storedItems && userEmail) {
          this.currentUser = storedItems.find(item => item.email === userEmail);
          console.log("Current user:", this.currentUser); // Debug log
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
    clearForm() {
      this.userData.name = '';
      this.userData.address = '';
      this.userData.email = '';
      this.userData.password = '';
      this.userData.age = 0;
    },
    checkLoggedIn() {
      // Check if user is logged in by looking at localStorage or session
      if (localStorage.getItem('isLoggedIn')) {
        this.loginForm = true; // Set to false to show logged-in view
      }
    },
    login() {
      // Validate email and password (you can use vuelidate or custom logic)
      const storedItems = JSON.parse(localStorage.getItem('itemsJson'));
      const user = storedItems.find(item => this.userData.email===item.email)
      if (user) {
        if (this.userData.email === user.email && this.userData.password === user.password) {
        // Redirect to home page (replace with your route)
      this.loginForm=false;
      } else {
        // Show invalid email or password message
        alert('Invalid credentials');
      }
    }else{
      alert("Data not found data against "+ this.userData.email);
    }
  },
      logout() {
    // Remove the logged-in user's email and other related data
    localStorage.removeItem('isLoggedIn'); // Remove login status
    localStorage.removeItem('userEmail'); // Remove the logged-in user's email, if stored
    // Remove any other user-specific data you might have
    localStorage.removeItem('userData');
  this.currentUser = null 
    window.location.reload(); 
    this.$router.push('/login');
  }
    }
  };
  </script>
  
  
  <style>
  .v-list-item-avatar {
    margin-right: 16px;
  }
  .image {
    width: 5%;
    margin-right: 65rem;
  }
  .navbar {
    margin-left: -8rem;
  }
  
  .custom-menu .v-list {
    background-color: #dc1717; /* Light gray background */
    border-radius: 18px; /* Rounded corners */
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2); /* Subtle shadow */
  }
  
  .custom-menu .menu-list-item {
    
    border-bottom: 1px solid #f30707; /* Divider line between items */
  }
  
  .custom-menu .menu-list-item:last-child {
    border-bottom: none; /* Remove bottom border for last item */
  }
  
  .menu-title {
    font-weight: bold;
    margin-left: 1rem;
    margin-right: 1rem;
    color: #df0c0c; /* Darker text for title */
  }
  
  .menu-subtitle {
    margin-bottom: 1rem;
    margin-left: .5rem;
    color: #ed0c0c; /* Lighter text for subtitle */
  }
  
  .menu-icon {
    color: #1976D2; /* Customize icon color */
  }
  .avatar{
    margin-left: 2.5rem; 
  }
  .logo{
    font-size: xx-large;
  }
  .logout-btn {
  color: blue;
  }
  </style>