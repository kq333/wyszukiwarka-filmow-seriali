<template>
  <v-app id="demo1">


    <v-main>
      <HelloWorld/>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>

<style >

#demo1{
  background-color:rgba(7, 6, 6, 0.315);
}

</style>
