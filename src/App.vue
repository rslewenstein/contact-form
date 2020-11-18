<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-text class="app-title">Contact Form</v-text>
      </div>

      <v-spacer></v-spacer>

      
    </v-app-bar>

    <v-main>
      <Form/>
    </v-main>
  </v-app>
</template>

<script>
import Form from './components/Form';

export default {
  name: 'App',

  components: {
    Form,
  },

  data: () => ({
    //
  }),
};
</script>

<style scoped>
.app-title{
  font-size: 40px;
  font-family: fantasy;
}
</style>