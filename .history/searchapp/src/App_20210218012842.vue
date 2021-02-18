<template>
  <v-app id="demo">


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

#demo{
  background-color:rgba(201, 89, 89, 0.342);
}

</style>
