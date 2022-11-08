<template>
  <div class="main-div">

    <!-- Tagline, description, buttons -->
    <v-row v-if="!isMobile">
      <v-col align-self="" class="left-col" cols="8">
        <p class="tagline">{{tagline}}</p>
        <p class="description"
          :style="{'font-size': windowWidth > 1400 ? '24px' : null}"
        >
          {{description}}
        </p>
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

    <!-- MOBILE: Tagline, picture -->
    <v-row v-else-if="isMobile">
      <v-col align-self="" class="left-col" cols="7">
        <p class="tagline"
          :style="{'font-size': '27px', 'line-height': '35px'}"
        >
          {{tagline}}
        </p>
      </v-col>
      <v-col class="right-col" cols="5">
        <img width="100%"
          src="~/assets/images/person.png"
        >
      </v-col>
    </v-row>

    <v-row v-if="isMobile">
      <v-col>
        <p class="description"
          :style="{'font-size': '18px'}"
        >
          {{description}}
        </p>
        <div class="btn-row text-center"
          :style="{'margin-top': '10%'}"
        >
          <a class="js-scroll-trigger" href="#signup">
            <v-btn class="join-button" color="#96FBC4">{{join}}</v-btn>
          </a>
          <v-btn class="nav-button" color="#2B2E36" to="/about">{{about}}</v-btn>
        </div>
      </v-col>
    </v-row>

    <!-- Feature cards -->
    <v-row class="card-row text-center" justify="center" v-if="!isMobile">
      <v-card class="feature-card"
        v-for="(feat, f) in featureCards" :key="f"
        width="200px"
      >
        <v-card-text class="card-title">
          <img :src="require(`~/assets/images/${feat.src}`)" width="70px" />
        </v-card-text>
        <v-card-text class="card-text">{{feat.description}}</v-card-text>
      </v-card>
    </v-row>

    <!-- MOBILE: feature cards -->
    <v-row class="card-row text-center" justify="center" v-else-if="isMobile">
      <v-col :style="{'justify-content': 'center', 'display': 'grid'}">
        <v-card class="feature-card"
          v-for="(feat, f) in featureCards" :key="f"
          :style="{'margin-top': '5%'}"
          width="200px"
        > <!-- height="250px" -->
          <v-card-text class="card-title">
            <img :src="require(`~/assets/images/${feat.src}`)" width="70px" />
          </v-card-text>
          <v-card-text class="card-text">{{feat.description}}</v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <!-- Quote -->
    <v-row class="quote-row" justify="center"
      :style="{'margin-top': isMobile ? '15%' : null, 'margin-bottom': isMobile ? '12%' : null}"
    >
      <p class="whole-quote text-center">
        <img class="open-quote"
          src="~/assets/images/open-quote.png"
          :style="{'max-width': isMobile ? '40px' : null}"
        />
        <span class="quote"
          :style="{'font-size': isMobile ? '20px' : null, 'margin-left': isMobile ? '10px' : null, 'margin-right': isMobile ? '10px' : null, 'width': isMobile ? '65%' : null}"
        >
          {{quote}}
        </span>
        <img class="close-quote"
          src="~/assets/images/close-quote.png"
          :style="{'max-width': isMobile ? '40px' : null}"
        />
      </p>
    </v-row>

    <!-- Signup cards -->
    <v-row class="signup-row text-center" id="signup" justify="center" v-if="!isMobile">
      <v-card class="signup-card">
        <div class="signup-card-content">
          <p class="signup-title">Candidate Sign-Up</p>
          <p class="signup-text">{{candidate}}</p>
          <v-btn class="engineer-join-button" color="#96FBC4" @click="launchCandidateSurvey()">{{candidateJoin}}</v-btn>
        </div>
      </v-card>

      <v-card class="signup-card">
        <div class="signup-card-content">
          <p class="signup-title">Recruiter Sign-Up</p>
          <p class="signup-text">{{recruiter}}</p>
          <v-btn outlines class="recruiter-join-button" @click="launchRecruiterSurvey()">{{recruiterJoin}}</v-btn>
        </div>
      </v-card>
    </v-row>

    <!-- MOBILE: Signup cards -->
    <v-row class="signup-row text-center" id="signup" justify="center" v-else>
      <v-col :style="{'justify-content': 'center', 'display': 'grid'}">
        <v-card class="signup-card">
          <div class="signup-card-content">
            <p class="signup-title">Candidate Sign-Up</p>
            <p class="signup-text">{{candidate}}</p>
            <v-btn class="engineer-join-button" color="#96FBC4" @click="launchCandidateSurvey()">{{candidateJoin}}</v-btn>
          </div>
        </v-card>

        <v-card class="signup-card">
          <div class="signup-card-content">
            <p class="signup-title">Recruiter Sign-Up</p>
            <p class="signup-text">{{recruiter}}</p>
            <v-btn outlines class="recruiter-join-button" @click="launchRecruiterSurvey()">{{recruiterJoin}}</v-btn>
          </div>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',

  created () {
    window.addEventListener('resize', this.resizeHandler)
  },

  data () {
    return {
      windowWidth: window.innerWidth,
      tagline: 'Only Get Offers You Love. Guaranteed.',
      description: 'Make Me Quit is a no-search employment platform for Software Engineers that allows you to passively receive great opportunities tailored to you. Create a profile in less than 5 minutes, name your price, and only get notified for offers that meet or exceed your standard. No spam. No headache. Welcome to the passive dream-job search.',
      join: 'Join Beta',
      about: 'About',
      featureCards: [
        {
          src: 'filter.png',
          description: 'Customize your criteria for offers you really, really want.\nNo. More. Spam.',
        },
        {
          src: 'money.png',
          description: 'Get job offers that fit your criteria and move you forward - without actively looking.',
        },
        {
          src: 'handshake.png',
          description: 'Total anonymity until you accept an invitation to interview.',
        }
      ],
      filter: 'Customize your criteria for offers you really, really want.\nNo. More. Spam.',
      offers: 'Get job offers that fit your criteria and move you forward - without actively looking.',
      anon: 'Total anonymity until you accept an invitation to interview.',
      quote: 'Awesome jobs don\'t come along every day. We\'re here to help you be ready when opportunity knocks.',
      candidate: 'Set your criteria, remain anonymous, get offers\n\n',
      recruiter: 'Get access to the best developers and see their price up front',
      candidateJoin: 'Join Engineer Beta',
      recruiterJoin: 'Join Recruiter Beta',
    }
  },

  methods: {
    async launchCandidateSurvey() {
      await open('https://qfreeaccountssjc1.az1.qualtrics.com/jfe/form/SV_6RIHUG9yhj9HPlY')
    },

    async launchRecruiterSurvey() {
      await open('https://forms.gle/mikpYKPUpCnPoT4E9')
    },

    resizeHandler() {
      this.windowWidth = window.innerWidth
    }
  },

  computed: {
    isMobile () {
      let check = false;
      (function(a){if(/(android|bb\d+|meego).+mobile|avantgo|bada\/|blackberry|blazer|compal|elaine|fennec|hiptop|iemobile|ip(hone|od)|iris|kindle|lge |maemo|midp|mmp|mobile.+firefox|netfront|opera m(ob|in)i|palm( os)?|phone|p(ixi|re)\/|plucker|pocket|psp|series(4|6)0|symbian|treo|up\.(browser|link)|vodafone|wap|windows ce|xda|xiino/i.test(a)||/1207|6310|6590|3gso|4thp|50[1-6]i|770s|802s|a wa|abac|ac(er|oo|s\-)|ai(ko|rn)|al(av|ca|co)|amoi|an(ex|ny|yw)|aptu|ar(ch|go)|as(te|us)|attw|au(di|\-m|r |s )|avan|be(ck|ll|nq)|bi(lb|rd)|bl(ac|az)|br(e|v)w|bumb|bw\-(n|u)|c55\/|capi|ccwa|cdm\-|cell|chtm|cldc|cmd\-|co(mp|nd)|craw|da(it|ll|ng)|dbte|dc\-s|devi|dica|dmob|do(c|p)o|ds(12|\-d)|el(49|ai)|em(l2|ul)|er(ic|k0)|esl8|ez([4-7]0|os|wa|ze)|fetc|fly(\-|_)|g1 u|g560|gene|gf\-5|g\-mo|go(\.w|od)|gr(ad|un)|haie|hcit|hd\-(m|p|t)|hei\-|hi(pt|ta)|hp( i|ip)|hs\-c|ht(c(\-| |_|a|g|p|s|t)|tp)|hu(aw|tc)|i\-(20|go|ma)|i230|iac( |\-|\/)|ibro|idea|ig01|ikom|im1k|inno|ipaq|iris|ja(t|v)a|jbro|jemu|jigs|kddi|keji|kgt( |\/)|klon|kpt |kwc\-|kyo(c|k)|le(no|xi)|lg( g|\/(k|l|u)|50|54|\-[a-w])|libw|lynx|m1\-w|m3ga|m50\/|ma(te|ui|xo)|mc(01|21|ca)|m\-cr|me(rc|ri)|mi(o8|oa|ts)|mmef|mo(01|02|bi|de|do|t(\-| |o|v)|zz)|mt(50|p1|v )|mwbp|mywa|n10[0-2]|n20[2-3]|n30(0|2)|n50(0|2|5)|n7(0(0|1)|10)|ne((c|m)\-|on|tf|wf|wg|wt)|nok(6|i)|nzph|o2im|op(ti|wv)|oran|owg1|p800|pan(a|d|t)|pdxg|pg(13|\-([1-8]|c))|phil|pire|pl(ay|uc)|pn\-2|po(ck|rt|se)|prox|psio|pt\-g|qa\-a|qc(07|12|21|32|60|\-[2-7]|i\-)|qtek|r380|r750|raks|rim9|ro(ve|zo)|s55\/|sa(ge|ma|mm|ms|ny|va)|sc(01|h\-|oo|p\-)|sdk\/|se(c(\-|0|1)|47|mc|nd|ri)|sgh\-|shar|sie(\-|m)|sk\-0|sl(45|id)|sm(al|ar|b3|it|t5)|so(ft|ny)|sp(01|h\-|v\-|v )|sy(01|mb)|t2(18|50)|t6(00|10|18)|ta(gt|lk)|tcl\-|tdg\-|tel(i|m)|tim\-|t\-mo|to(pl|sh)|ts(70|m\-|m3|m5)|tx\-9|up(\.b|g1|si)|utst|v400|v750|veri|vi(rg|te)|vk(40|5[0-3]|\-v)|vm40|voda|vulc|vx(52|53|60|61|70|80|81|83|85|98)|w3c(\-| )|webc|whit|wi(g |nc|nw)|wmlb|wonu|x700|yas\-|your|zeto|zte\-/i.test(a.substr(0,4))) check = true;})(navigator.userAgent||navigator.vendor||window.opera);
      return check;
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
    color: #eaeaea;
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
    background-color: #2B2E36;
    /* opacity: 0.6; */
    border-radius: 6px;
    margin-right: 5%;
}

.signup-card-content {
    margin: 30px 0px;
}

.signup-title {
    font-family: 'Lexend Deca';
    font-style: normal;
    font-weight: 700;
    font-size: 24px;
    line-height: 30px;
    color: #eaeaea;
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
    color: #eaeaea;
}

</style>
