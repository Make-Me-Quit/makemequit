<template>
  <div class="main-div">
    <v-row>
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

    <v-row class="card-row text-center" justify="center">
      <v-card class="feature-card" width="200px">
        <v-card-title class="card-title">
          <img src="~/assets/images/filter.png" width="70px"/>
        </v-card-title>
        <v-card-text class="card-text">{{filter}}</v-card-text>
      </v-card>

      <v-card class="feature-card" width="200px">
        <v-card-title class="card-title">
          <img src="~/assets/images/dollar.png" width="70px"/>
        </v-card-title>
        <v-card-text class="card-text">{{offers}}</v-card-text>
      </v-card>

      <v-card class="feature-card" width="200px">
        <v-card-title class="card-title">
          <img src="~/assets/images/handshake.png" width="70px"/>
        </v-card-title>
        <v-card-text class="card-text">{{anon}}</v-card-text>
      </v-card>
    </v-row>

    <v-row class="quote-row" justify="center">
      <p class="whole-quote text-center">
        <img class="open-quote" src="~/assets/images/open-quote.png" />
        <span class="quote">{{quote}}</span>
        <img class="close-quote" src="~/assets/images/close-quote.png" />
      </p>
    </v-row>

    <v-row class=" signup-row text-center" justify="center">
      <v-card class="signup-card">
        <div class="signup-card-content">
          <p class="signup-title">Candidate Sign-Up</p>
          <p class="signup-text">{{candidate}}</p>
          <v-btn class="engineer-join-button" color="#96FBC4" to="/join">{{candidateJoin}}</v-btn>
        </div>
      </v-card>

      <v-card class="signup-card">
        <div class="signup-card-content">
          <p class="signup-title">Recruiter Sign-Up</p>
          <p class="signup-text">{{recruiter}}</p>
          <v-btn
            depressed
            outlined
            class="recruiter-join-button"
            to="/join"
          >
            {{recruiterJoin}}
          </v-btn>
        </div>
      </v-card>
    </v-row>
  </div>
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
      filter: 'Customize your criteria for offers you really, really want.\nNo. More. Spam.',
      offers: 'Get job offers that fit your criteria and move you forward - without actively looking.',
      anon: 'Total anonymity until you accept an offer.\nTeam #quietquit',
      quote: 'Awesome jobs don\'t come along every day. We\'re here to help you be ready when opportunity knocks.',
      candidate: 'Set your criteria, remain anonymous, get offers\n\n',
      recruiter: 'Get access to the best developers and see their price up front',
      candidateJoin: 'Join Engineer Beta',
      recruiterJoin: 'Join Recruiter Beta',
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
