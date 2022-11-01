<template>
  <v-col class="text-center">
    <h2 class="text">Meet our team!</h2>
    <v-row class="picture-row text-center" justify="center" align="center">
      <v-col v-for="(person, i) in team" :key="i">
        <img class="team-img" :src="require(`~/assets/images/${person.img}.jpg`)" />
        <v-spacer />
        <span class="text">{{person.name}}</span>
        <v-spacer />
        <span class="text">{{person.role}}</span>
      </v-col>
    </v-row>
  </v-col>
</template>

<script>
export default {
  name: 'AboutPage',

  data () {
    return {
      team: [
        {
          name: 'Jack Morgan',
          img: 'jack',
          role: 'Product Manager',
        },
        {
          name: 'Andrew Thibaudeau',
          img: 'andrew',
          role: 'Software Engineer',
        },
        {
          name: 'Travis Reynertson',
          img: 'travis',
          role: 'Software Engineer',
        },
        {
          name: 'Wyatt Thacker',
          img: 'wyatt',
          role: 'UX Designer',
        }
      ]
    }
  }
}
</script>

<style scoped>
@import '~/assets/style.css';

.picture-row {
  margin-top: 20px;
}

.team-img {
  border-radius: 50%;
  width: 200px;
  /* margin: 10px 10px; */
}
.text {
  font-family: 'Lexend Deca';
  color: #eaeaea;
}

</style>
