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
            <v-spacer />
            <v-btn color="yellow" style="color: black" nuxt> გაგზავნა </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: 'Registration',
  data() {
    return {
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
    }
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
