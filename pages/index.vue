<template>
  <div class="main-div">

    <!-- Tagline, description, buttons -->
    <v-row>
      <v-col align-self="" class="left-col" cols="8">
        <p class="tagline">{{tagline}}</p>
        <p class="description">{{description}}</p>
        <div class="btn-row">
        <a class="js-scroll-trigger" href="#signup">
          <v-btn class="join-button" color="#96FBC4">{{join}}</v-btn>
        </a>
        <v-btn class="nav-button" color="#2B2E36" to="/about">{{about}}</v-btn>
        </div>
      </v-col>
      <v-col class="right-col" cols="4">
        <img width="100%"
          src="~/assets/images/person.png"
        >
      </v-col>
    </v-row>

    <!-- Feature cards -->
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

    <!-- Quote -->
    <v-row class="quote-row" justify="center">
      <p class="whole-quote text-center">
        <img class="open-quote" src="~/assets/images/open-quote.png" />
        <span class="quote">{{quote}}</span>
        <img class="close-quote" src="~/assets/images/close-quote.png" />
      </p>
    </v-row>

    <!-- Signup cards -->
    <v-row class=" signup-row text-center" id="signup" justify="center">
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

.btn-row {
  margin-top: 5%;
}

.join-button {
  margin-right: 1%;
  color: #111111;
}

.nav-button {
  width: 150px;
}

.tagline {
    font-family: 'Lexend Deca';
    font-style: normal;
    font-weight: 400;
    font-size: 60px;
    line-height: 70px;

    background: linear-gradient(134.94deg, #96FBC4 4.82%, #ACFCB2 29.27%, #C5FBA0 56.61%, #DEF991 70.28%, #F9F586 78.15%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.description {
    font-family: 'Lexend Deca';
    font-style: normal;
    font-weight: 400;
    font-size: 20px;
    line-height: 150%;
    color: #eaeaea;
}

.main-div {
    margin-left: 3%;
    margin-right: 3%;
    margin-top: 2%;
}

.card-row {
    margin-top: 6%;
    margin-bottom: 6%;
}

.feature-card {
    background-color: #2B2E36;
    margin-right: 5%;
}

.card-title {
    justify-content: center;
}

.card-text {
    white-space: pre-wrap;
    font-family: 'Lexend Deca';
    font-style: normal;
    font-weight: 400;
    font-size: 15px;
    line-height: 150%;
    color: #ffffff;
}

.quote-row {
    margin-top: 8%;
    margin-bottom: 8%;
}

.whole-quote {
    justify-content: center;
}

.open-quote {
    vertical-align: top;
    max-width: 80px;
    max-height: 57px;
    height: auto;
    width: auto;
}

.close-quote {
    vertical-align: bottom;
    max-width: 80px;
    max-height: 57px;
    height: auto;
    width: auto;
}

.quote {
    margin-left: 20px;
    margin-right: 20px;
    display: inline-block;
    width: 60%;
    font-family: 'Lexend Deca';
    font-style: normal;
    font-weight: 400;
    font-size: 26px;
    line-height: 150%;
    color: #eaeaea;
}

.signup-row {
    margin-bottom: 5%;
}

.signup-card {
    border-width: 2px;
    border-style: solid;
    border-image: linear-gradient(134.94deg, #96FBC4 4.82%, #ACFCB2 29.27%, #C5FBA0 56.61%, #DEF991 70.28%, #F9F586 78.15%) 1;
    margin-bottom: 20px;
    width: 350px;
    background: #2B2E36;
    opacity: 0.6;
    border-radius: 6px;
    margin-right: 5%;
}

.signup-card-content {
    margin-top: 30px;
    margin-bottom: 30px;
}

.signup-title {
    font-family: 'Lexend Deca';
    font-style: normal;
    font-weight: 700;
    font-size: 24px;
    line-height: 30px;
    color: #FFFFFF;
}

.signup-text {
    white-space: pre-wrap;
    display: inline-block;
    width: 200px;
    font-family: 'Lexend Deca';
    font-style: normal;
    font-weight: 200;
    font-size: 16px;
    line-height: 150%;
    color: #FFFFFF;
}

</style>
