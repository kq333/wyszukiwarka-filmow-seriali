<template>
  <v-container>


<div id="demo">




<v-row color="red" >
   <v-col lg="10">


            <v-text-field  clearable placeholder="wpisz cos" type="text" v-model="input"></v-text-field>

    </v-col>

    <v-btn depressed @click="klik" class="mt-4"><v-icon>mdi-apple </v-icon>Szukaj</v-btn>

 </v-row>



  <v-row>
    <v-col >
      <div   v-for="arr in arrays" :key="arr.index" >
        <p>Tytuł:{{arr.title}}</p>
        <p> Aktorzy:  {{ arr.actors}}</p>
         <p>  Reżyseria:{{arr.director}}</p>
      <img style="border-radius: 2%"  :src="arr.poster" />

      </div>
    </v-col>
  </v-row>


 </div>





  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data(){

    return{

      input:'',

      arrays:[],
    }

  },
   methods: {

      klik(){
       this.input





 const url = 'https://www.omdbapi.com/?apikey=7bd5b2c8&t=';

    const result  = url + this.input;
    fetch(result)

  .then((res)=>{
      return res.json();
  })

  .then((data)=>{

    console.log(data)



    this.arrays.push({poster: data.Poster, actors: data.Actors, director: data.Director, title:data.Title,})


  }),

this.input=''

      }}}


</script>
