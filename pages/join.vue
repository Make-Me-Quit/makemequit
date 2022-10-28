<template>
  <v-app>
    <!-- Google tag (gtag.js) -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=G-6H8LGG4D7G"></script>
    <script>
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());

      gtag('config', 'G-6H8LGG4D7G');
    </script>
    <v-row justify="center" align="center">
      <h2>Welcome! Join our Beta test here!</h2>
    </v-row>
  </v-app>
</template>

<script>
export default {
  name: 'JoinPage'
}
</script>
