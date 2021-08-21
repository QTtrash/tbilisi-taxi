<template>
  <div class="registration-image">
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <v-card>
          <v-card-title class="headline"> რეგისტრაცია </v-card-title>
          <v-card-text>
            <v-text-field
              v-model="fullname"
              color="yellow"
              label="სახელი და გვარი"
            />
          </v-card-text>
          <v-card-text>
            <v-text-field
              v-model="birthday"
              color="yellow"
              label="დაბადების თარიღი"
            />
          </v-card-text>
          <v-card-text>
            <v-text-field
              v-model="phoneNumber"
              color="yellow"
              label="მობილურის ნომერი"
            />
          </v-card-text>
          <v-card-text>
            <v-text-field
              v-model="passNumber"
              color="yellow"
              label="მართვის მოწმობის სერია და ნომერი"
            />
          </v-card-text>
          <v-card-text>
            <v-text-field
              v-model="passRegDate"
              color="yellow"
              label="მართვის მოწმობის აღების თარიღი"
            />
          </v-card-text>
          <v-card-text>
            <v-text-field
              v-model="passValidDate"
              color="yellow"
              label="მართვის მოწმობის მოქმედების ვადა"
            />
          </v-card-text>
          <v-card-text>
            <v-text-field
              v-model="car"
              color="yellow"
              label="ავტომობილის მარკა"
            />
          </v-card-text>
          <v-card-text>
            <v-text-field
              v-model="carModel"
              color="yellow"
              label="ავტომობილის მოდელი"
            />
          </v-card-text>
          <v-card-text>
            <v-text-field
              v-model="carColor"
              color="yellow"
              label="ავტომობილის ფერი"
            />
          </v-card-text>
          <v-card-text>
            <v-text-field
              v-model="carDate"
              color="yellow"
              label="ავტომობილის გამოშვების წელი"
            />
          </v-card-text>
          <v-card-text>
            <v-text-field
              v-model="carId"
              color="yellow"
              label="ავტომობილის სახელმწოფო ნომერი"
            />
          </v-card-text>
          <v-card-text>
            <v-text-field v-model="city" color="yellow" label="ქალაქი" />
          </v-card-text>
          <v-card-actions>
            <diamond v-if="loading" />
            <v-spacer />
            <v-card-text v-if="loading"> გთხოვთ დაელოდოთ </v-card-text>
            <v-spacer />
            <v-card-text v-if="error">
              გთხოვთ დაუკავშირდეთ ჩვენს წარმომადგენელს <br />
              +995 597037341
            </v-card-text>
            <v-spacer />
            <v-btn
              color="yellow"
              :disabled="loading"
              style="color: black"
              @click="sendUserInfo"
            >
              გაგზავნა
            </v-btn>
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
  name: 'Registration',
  components: {
    Diamond,
  },
  data() {
    return {
      loading: false,
      error: false,
      fullname: '',
      birthday: '',
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
    }
  },
  methods: {
    async sendUserInfo() {
      const headers = {
        'Content-Type': 'application/json',
      }

      this.loading = true
      this.error = false

      await axios
        .post(
          'https://taxi-tbilisi-backend.herokuapp.com/users',
          {
            fullname: this.fullname,
            birthday: this.birthday,
            phoneNumber: this.phoneNumber,
            passNumber: this.passNumber,
            passRegDate: this.passRegDate,
            passValidDate: this.passValidDate,
            car: this.car,
            carModel: this.carModel,
            carColor: this.carColor,
            carDate: this.carDate,
            carId: this.carId,
            city: this.city,
          },
          {
            headers,
          }
        )
        .then((res) => {
          this.router = false
          this.error = false
          this.$router.push({ path: 'complete' })
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
.registration-image {
  background-image: url('/background-reg.jpeg');
  background-position: center;
  background-size: cover;
}
</style>
