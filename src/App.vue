<template>
  <v-app>
    <v-content>
      <HelloWorld/>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data () {
    return {
      //
    }
  }
}
</script>

<style>
  body {
    margin: 0;
    margin-top: 10px;
    color: #333 !important;
    font-family: "Open Sans", "Source Sans Pro", sans-serif !important;
    font-weight: 400;
    line-height: 1.6;
  }
/* override vuetify cannot guarantee that this is "best practice" */
  .application {
    font-family: "Open Sans", "Source Sans Pro", sans-serif !important;
}
.theme--light .v-toolbar {
  background-color: #ffffff !important;
}

</style>



