<template>
  <div class="complete-image">
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="8">
        <v-card>
          <v-data-table
            :headers="headers"
            :items="clients"
            :items-per-page="5"
            class="elevation-1"
          ></v-data-table>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Registration',
  data() {
    return {
      headers: [
        { text: 'სახელი', value: 'fullname' },
        { text: 'მობილურის ნომერი', value: 'phonenumber' },
        { text: 'მართვის მოწმობის სერია და ნომერი', value: 'passnumber' },
        { text: 'მართვის მოწმობის აღების თარიღი', value: 'passregdate' },
        { text: 'მართვის მოწმობის მოქმედების ვადა', value: 'passvaliddate' },
        { text: 'ავტომობილის მარკა', value: 'car' },

        { text: 'ავტომობილის მოდელი', value: 'carmodel' },
        { text: 'ავტომობილის ფერი', value: 'carcolor' },
        { text: 'ავტომობილის გამოშვების წელი', value: 'cardate' },
        { text: 'ავტომობილის სახელმწოფო ნომერი', value: 'carid' },
        { text: 'ქალაქი', value: 'city' },
      ],
      fullname: '',
      phoneNumber: '',
      passNumber: '',
      passRegDate: '',
      passValidDate: '',
      car: '',
      carModel: '',
      carColor: '',
      carDate: '',
      carId: '',
      city: '',
      clients: [],
    }
  },
  created() {
    this.getUserInfo()
  },
  methods: {
    async getUserInfo() {
      await axios
        .get('https://taxi-tbilisi-backend.herokuapp.com/users')
        .then((res) => {
          const { data } = res
          this.clients = data
        })
    },
  },
}
</script>

<style>
.complete-image {
  background-image: url('/background-reg.jpeg');
  background-position: center;
  background-size: cover;
  height: 85vh;
}
</style>
