<template>
  <v-col class="text-center">
    <span class="about-header">Our Team</span>
    <!-- Team pictures -->
    <v-row class="picture-row text-center" justify="center" align="center">
      <v-card class="team-card"
        v-for="(person, i) in team" :key="i"
        width="200px"
      >
        <div class="team-card-content">
          <img class="team-img" :src="require(`~/assets/images/${person.imgBlob}`)" width="150px" />
          <v-spacer />
          <span class="name-text">{{person.name}}</span>
          <v-spacer />
          <span class="role-text">{{person.role}}</span>
        </div>
      </v-card>
    </v-row>

    <!-- Background, Product Description -->
    <v-row class="background-row" justify="center"
      :style="{'margin-top': isMobile ? '15%' : null, 'margin-bottom': isMobile ? '12%' : null}"
    >
      <p>
        <img class="handshake-lg"
          src="~/assets/images/handshake-lg.png"
          :style="{'max-width': isMobile ? '50px' : null}"
        />
        <span class="background"
          :style="{'font-size': isMobile ? '18px' : null, 'margin-left': isMobile ? '10px' : null, 'margin-right': isMobile ? '10px' : null, 'width': isMobile ? '65%' : null}"
        >
          <span :style="{'text-decoration': 'underline', 'font-size': isMobile ? '22px' : '26px'}">Background</span>
          <v-spacer />
          {{background}}
          <br><br>
          <span :style="{'text-decoration': 'underline', 'font-size': isMobile ? '22px' : '26px'}">Our Product</span>
          <v-spacer />
          {{product}}
        </span>
        <img class="dollar"
          src="~/assets/images/dollar.png"
          :style="{'max-width': isMobile ? '50px' : null}"
        />
      </p>
    </v-row>

    <!-- Reach out -->
    <span class="about-header">Reach Out!</span>
    <v-spacer />
    <div class="reach-out-text">
      <span>{{reachOut}}</span>
    </div>
    <!-- Form -->
    <v-row justify="center">
      <v-card class="form-card">
        <!-- <div class="form-content"
          :style="{'margin': isMobile ? '30px 20px' : null}"
        > -->
        <form class="form-content"
          action="https://submit-form.com/5zSoLWvH"
          :style="{'margin': isMobile ? '30px 20px' : null}"
        >
          <input type="hidden" name="_redirect" value="https://makemequit.dev/about" />
          <v-row>
            <input type="text" class="text-field" v-model="name" name="name" placeholder="Name" required>
            <input type="email" class="text-field" v-model="email" name="email" placeholder="Email" required>
          </v-row>
          <textarea type="text"
            class="text-area"
            v-model="message"
            name="message"
            rows="5"
            placeholder="Your message here..."
            required
          ></textarea>
          <v-btn
            class="send-btn"
            type="submit"
          >
            Send
            <v-icon right>mdi-send</v-icon>
          </v-btn>
        </form>
        <!-- </div> -->
      </v-card>
    </v-row>
  </v-col>
</template>

<script>
export default {
  name: 'AboutPage',

  mounted () {
    if (this.$route.params.email != undefined) {
      alert('Thank you for your submission! We will get back to you as soon as we can.')
    }
  },

  data () {
    return {
      team: [
        {
          name: 'Jack Morgan',
          img: 'jack.jpg',
          imgBlob: 'jack-blob.png',
          role: 'Product Manager',
        },
        {
          name: 'Andrew Thibaudeau',
          img: 'andrew.jpg',
          imgBlob: 'andrew-blob.png',
          role: 'Software Engineer',
        },
        {
          name: 'Travis Reynertson',
          img: 'travis.jpg',
          imgBlob: 'travis-blob.png',
          role: 'Software Engineer',
        },
        {
          name: 'Wyatt Thacker',
          img: 'wyatt.jpg',
          imgBlob: 'wyatt-blob.png',
          role: 'UX Designer',
        }
      ],
      background: 'We are all students at BYU in the Sandbox 02 Program, a startup incubator sponsored by the Rollins Center. We spent weeks speaking to software engineers and recruiters as we searched for a way to improve the hiring experience for those with experience.',
      product: 'It\'s pretty obvious that the hiring process is messy. Recruiters spam employees, employees get messages they\'re not interested in, and the circle continues. We wanted to empower employees to receive only offers that might be interesting to them, which led to our product - Make Me Quit!',
      reachOut: 'We would love to hear from you! Feel free to share suggestions, feedback, and excitement.',
      name: '',
      email: '',
      message: '',
    }
  },

  methods : {
    // async sendEmail() {
    //   try {
    //     await emailjs.send('mmq_gmail_service', 'contact_form', {
    //       from_name: this.name,
    //       from_email: this.email,
    //       message: this.message,
    //     },
    //     'rWfLyPQyBNY3WqQSS')
    //   } catch (error) {
    //     console.log('Failed...', error)
    //   }
    // }
  },

  computed: {
    isMobile () {
      let check = false;
      (function(a){if(/(android|bb\d+|meego).+mobile|avantgo|bada\/|blackberry|blazer|compal|elaine|fennec|hiptop|iemobile|ip(hone|od)|iris|kindle|lge |maemo|midp|mmp|mobile.+firefox|netfront|opera m(ob|in)i|palm( os)?|phone|p(ixi|re)\/|plucker|pocket|psp|series(4|6)0|symbian|treo|up\.(browser|link)|vodafone|wap|windows ce|xda|xiino/i.test(a)||/1207|6310|6590|3gso|4thp|50[1-6]i|770s|802s|a wa|abac|ac(er|oo|s\-)|ai(ko|rn)|al(av|ca|co)|amoi|an(ex|ny|yw)|aptu|ar(ch|go)|as(te|us)|attw|au(di|\-m|r |s )|avan|be(ck|ll|nq)|bi(lb|rd)|bl(ac|az)|br(e|v)w|bumb|bw\-(n|u)|c55\/|capi|ccwa|cdm\-|cell|chtm|cldc|cmd\-|co(mp|nd)|craw|da(it|ll|ng)|dbte|dc\-s|devi|dica|dmob|do(c|p)o|ds(12|\-d)|el(49|ai)|em(l2|ul)|er(ic|k0)|esl8|ez([4-7]0|os|wa|ze)|fetc|fly(\-|_)|g1 u|g560|gene|gf\-5|g\-mo|go(\.w|od)|gr(ad|un)|haie|hcit|hd\-(m|p|t)|hei\-|hi(pt|ta)|hp( i|ip)|hs\-c|ht(c(\-| |_|a|g|p|s|t)|tp)|hu(aw|tc)|i\-(20|go|ma)|i230|iac( |\-|\/)|ibro|idea|ig01|ikom|im1k|inno|ipaq|iris|ja(t|v)a|jbro|jemu|jigs|kddi|keji|kgt( |\/)|klon|kpt |kwc\-|kyo(c|k)|le(no|xi)|lg( g|\/(k|l|u)|50|54|\-[a-w])|libw|lynx|m1\-w|m3ga|m50\/|ma(te|ui|xo)|mc(01|21|ca)|m\-cr|me(rc|ri)|mi(o8|oa|ts)|mmef|mo(01|02|bi|de|do|t(\-| |o|v)|zz)|mt(50|p1|v )|mwbp|mywa|n10[0-2]|n20[2-3]|n30(0|2)|n50(0|2|5)|n7(0(0|1)|10)|ne((c|m)\-|on|tf|wf|wg|wt)|nok(6|i)|nzph|o2im|op(ti|wv)|oran|owg1|p800|pan(a|d|t)|pdxg|pg(13|\-([1-8]|c))|phil|pire|pl(ay|uc)|pn\-2|po(ck|rt|se)|prox|psio|pt\-g|qa\-a|qc(07|12|21|32|60|\-[2-7]|i\-)|qtek|r380|r750|raks|rim9|ro(ve|zo)|s55\/|sa(ge|ma|mm|ms|ny|va)|sc(01|h\-|oo|p\-)|sdk\/|se(c(\-|0|1)|47|mc|nd|ri)|sgh\-|shar|sie(\-|m)|sk\-0|sl(45|id)|sm(al|ar|b3|it|t5)|so(ft|ny)|sp(01|h\-|v\-|v )|sy(01|mb)|t2(18|50)|t6(00|10|18)|ta(gt|lk)|tcl\-|tdg\-|tel(i|m)|tim\-|t\-mo|to(pl|sh)|ts(70|m\-|m3|m5)|tx\-9|up(\.b|g1|si)|utst|v400|v750|veri|vi(rg|te)|vk(40|5[0-3]|\-v)|vm40|voda|vulc|vx(52|53|60|61|70|80|81|83|85|98)|w3c(\-| )|webc|whit|wi(g |nc|nw)|wmlb|wonu|x700|yas\-|your|zeto|zte\-/i.test(a.substr(0,4))) check = true;})(navigator.userAgent||navigator.vendor||window.opera);
      return check;
    }
  },
}
</script>

<style scoped>
@import '~/assets/style.css';

.about-header {
  /* margin-top: 10px; */
  font-family: 'Lexend Deca';
  font-style: normal;
  font-weight: 400;
  font-size: 65px;
  line-height: 150%;
  /* identical to box height */
  text-align: center;
  background: linear-gradient(134.94deg, #96FBC4 4.82%, #ACFCB2 29.27%, #C5FBA0 56.61%, #DEF991 70.28%, #F9F586 78.15%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  /* text-fill-color: transparent; */
}

.picture-row {
  margin-top: 30px;
}

.team-card {
  background-color: #2B2E36;
  margin-right: 20px;
  margin-bottom: 20px;
}

.team-card-content {
  margin: 20px 0px;
}

.name-text {
  font-family: 'Lexend Deca';
  font-style: normal;
  font-weight: 600;
  font-size: 16px;
  line-height: 150%;
  text-align: center;
  color: #eaeaea;
}

.role-text {
  font-family: 'Lexend Deca';
  font-style: normal;
  /* font-weight: 600; */
  font-size: 15px;
  line-height: 150%;
  color: #eaeaea;
}

.background-row {
    margin-top: 5%;
    margin-bottom: 5%;
}

.handshake-lg {
    vertical-align: top;
    max-width: 120px;
    /* max-height: 57px; */
    height: auto;
    width: auto;
}

.dollar {
    vertical-align: bottom;
    max-width: 120px;
    /* max-height: 57px; */
    height: auto;
    width: auto;
}

.background {
    margin-left: 20px;
    margin-right: 20px;
    display: inline-block;
    text-align: left;
    width: 60%;
    font-family: 'Lexend Deca';
    font-style: normal;
    font-weight: 400;
    font-size: 20px;
    line-height: 150%;
    color: #eaeaea;
}

.reach-out-text {
  width: 325px;
  display: inline-block;
  font-family: 'Lexend Deca';
  font-style: normal;
  font-weight: 200;
  font-size: 14px;
  line-height: 150%;
  text-align: center;
  color: #eaeaea;
}

.form-card {
  margin: 50px 0px;
  justify-content: center;
  background: #2B2E36;
  border-radius: 6px;
  width: 700px;
}

.form-content {
  margin: 30px 50px;
  display: grid;
}

.text-field {
  width: 46%;
  margin: 2%;
  padding: 6px 6px;
  background-color: #fcfcfc !important;
  border-style: solid;
  border-width: 3px;
  border-image: linear-gradient(134.94deg, #96FBC4 4.82%, #ACFCB2 29.27%, #C5FBA0 56.61%, #DEF991 70.28%, #F9F586 78.15%) 1;
}

.text-area {
  border-style: solid;
  border-width: 3px;
  border-image: linear-gradient(134.94deg, #96FBC4 4.82%, #ACFCB2 29.27%, #C5FBA0 56.61%, #DEF991 70.28%, #F9F586 78.15%) 1;
  background-color: #fcfcfc !important;
  margin: 10px 0px;
  padding: 6px 6px;
}

.send-btn {
  justify-self: end;
  background-color: #96FBC4 !important;
  border-radius: 6px;
  width: 150px;
  font-family: 'Lexend Deca';
  font-style: normal;
  font-weight: 700;
  font-size: 16px;
  line-height: 150%;
  color: #000000;
}

</style>
