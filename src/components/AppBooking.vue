<template>
  <div class="home">
    <app-toolbar></app-toolbar>
    <v-container>
      <h1>Booking information</h1>
      <v-alert
      type="success" v-if="message !=''">{{message}}</v-alert><v-alert
      type="error"
      v-if="error !=''"
      >{{error}}</v-alert>
      <v-card class="p-5">
        <v-text-field
        label="Name"
        v-model="name"
        ></v-text-field>
        <v-row>
          <v-col cols = "6">
            <v-text-field
            type="email"
            label="Email"
            v-model="email"
            ></v-text-field>
          </v-col>
          <v-col cols="6">
            <v-text-field
            type="phone"
            label="Phone Number"
            v-model="phone"
            ></v-text-field>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="6">
            <v-text-field
            type="date"
            label="Pick-up date"
            v-model="senddate"
            ></v-text-field>
          </v-col>
          <v-col cols="6">
            <v-text-field
            type="date"
            label="Return date"
            v-model="returndate"
            ></v-text-field>
          </v-col>
        </v-row>
        <v-select
        :items="items"
        label="Pick-up location"
        v-model="sendplace"
        ></v-select>
        <v-select
        :items="items"
        label="Drop-off location"
        v-model="returnplace"
        ></v-select>

        <v-btn block color="primary" 
        v-on:click="buttonPress" 
        :loading="loading"
        >Book my car</v-btn>

      </v-card>


    </v-container>
    <app-footer></app-footer>

  </div>

  
</template>

<script>

import AppFooter from './AppFooter.vue';
import AppToolbar from './AppToolbar.vue';
export default {
  name: 'AppBooking',
  components: {AppFooter, AppToolbar},
  data(){
    return{
      items:["Putrajaya","Cyberjaya","Bangi"],
      name:'',
      email:'',
      phone:'',
      senddate:'',
      returndate:'',
      sendplace:'',
      returnplace:'',
      message:'',
      error:'',
      loading:'false'

    }
  },
  methods: {
    buttonPress:function(){

      let url = 'https://api.sheety.co/9afc2b77b3905050807b1c1d0567581f/bookingSheets/sheet1';
      let body = {
        sheet1: {
          name:this.name,
          email:this.email,
          phone:this.phone,
          senddate:this.senddate,
          returndate:this.returndate,
          sendplace:this.sendplace,
          returnplace:this.returnplace
        }
      }
      this.loading = true;
      fetch(url, {
        headers:{'Content-Type': 'application/json'},
        method: 'POST',
        body: JSON.stringify(body)
      })
      .then((response) => response.json())
      .then(json => {
      this.loading = false;
  // Do something with object
  if(json.sheet1){
    this.message = "Successfully booked. We will contact you soon."
  }
  else {
    this.error = json.errors[0]["detail"]
  }
});
    }
  }
}

</script>


