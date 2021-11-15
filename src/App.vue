<template>
  <v-app>
    <v-main>
      <Header title="Personal Info Form" />
      <Form />
    </v-main>
  </v-app>
</template>

<script>
import Header from "./components/Header.vue"
import Form from "./components/Form.vue"

export default {
  name: 'App',

  components: {
    Header,
    Form
  },

  data: () => ({
    //
  }),
};
</script>
