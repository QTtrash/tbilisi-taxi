<template>
  <div class="background-image">
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <v-card>
          <v-card-title class="headline"> Yandex Taxi </v-card-title>
          <v-card-text>
            <p>Tut budet tesli opisanie</p>
          </v-card-text>
          <v-card-actions>
            <v-spacer />
            <v-btn color="yellow" style="color: black" nuxt to="/registration">
              რეგისტრაცია
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<style>
.background-image {
  background-image: url('/background.jpeg');
  background-position: center;
  background-size: cover;
  height: 85vh;
}
</style>
