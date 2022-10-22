<template>
  <v-row class="row">
      <v-col align-self="" class="left-col" cols="8">
        <p class="tagline">{{tagline}}</p>
        <p class="description">{{description}}</p>
        <v-btn class="join-button" color="#96FBC4" to="/join">{{join}}</v-btn>
        <v-btn class="nav-button" color="#2B2E36" to="/about">{{about}}</v-btn>
      </v-col>
      <v-col class="right-col" cols="4">
        <img width="100%"
          src="~/assets/images/person.png"
        >
      </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage',

  data () {
    return {
      tagline: 'Only Get Offers You Love. Guaranteed.',
      description: 'Make Me Quit is a no-search employment platform that allows you to passively receive great opportunities tailored to you. Create a profile in less than 5 minutes, name your price, and only get notified for offers that meet or exceed your standard. No spam. No headache. Welcome to the passive dream-job search.',
      join: 'Join Beta',
      about: 'About Us',
    }
  }
}
</script>

<style scoped>
@import '~/assets/style.css';

.join-button {
  margin-top: 3%;
  margin-right: 1%;
}

.nav-button {
  margin-top: 3%;
  width: 150px;
  color: #eaeaea;
}

</style>
