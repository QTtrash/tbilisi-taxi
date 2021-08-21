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
          <v-card-actions>
            <diamond v-if="loading" />
            <v-spacer />
            <v-card-text v-if="loading"> გთხოვთ დაელოდოთ </v-card-text>
            <v-spacer />
            <v-card-text v-if="error">
              Please contact our lovely developer <br />
              @ Pornhub (special clients only) @ Facebook (friends only) @
              smouchsiadis@gmail.com
            </v-card-text>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import axios from 'axios'
import { Diamond } from 'vue-loading-spinner'

export default {
  name: 'DavidAdmin',
  components: {
    Diamond,
  },
  data() {
    return {
      loading: true,
      error: false,
      headers: [
        { text: 'სახელი და გვარი', value: 'fullname' },
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
      clients: [],
    }
  },
  created() {
    this.getUserInfo()
  },
  methods: {
    async getUserInfo() {
      this.loading = true
      this.error = false

      await axios
        .get('https://taxi-tbilisi-backend.herokuapp.com/users')
        .then((res) => {
          const { data } = res
          this.loading = false
          this.error = false
          this.clients = data
        })
        .catch((error) => {
          this.error = true
          this.loading = false
          throw error
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
