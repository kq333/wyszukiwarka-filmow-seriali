<template>
  <v-container>


<div id="demo">




<v-row color="red" >
   <v-col lg="10">


            <v-text-field  clearable placeholder="wpisz cos" type="text" v-model="input"></v-text-field>

    </v-col>

    <v-btn id="btn" outlined @click="klik" class="mt-4"><v-icon>mdi-find</v-icon>Szukaj</v-btn>

 </v-row>



  <v-row>
    <v-col >
      <div   v-for="arr in arrays" :key="arr.index" >
        <v-row>
          <v-col >
                <p  id="text1"  class="mx-12" style="font-size:38px">{{arr.title}}</p>
          </v-col>

                </v-row>

                  <v-row >
                    <v-col id="image"  lg="4" xs="2" >
                      <img  style="border-radius: 2%" class="ml-8" :src="arr.poster" />
                    </v-col>
                        <v-col id="text" lg="8" xs="2" cols="6" >
                          <p id="demo"> Aktorzy:  {{ arr.actors}}</p>
                          <p> Reżyseria: {{arr.director}}</p>
                          <p>Kraj: {{arr.country}}</p>
                          <p>Rok produkcji: {{arr.released}}</p>
                          <p>Gatunek: {{arr.genre}}</p>
                          <p>Opis: {{arr.plote}}</p>
                          <p>Ranking IMDB: {{arr.imdb}}</p>
                        </v-col>
                  </v-row>

              <v-row >

              </v-row>





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


/* const button = document.getElementById("btn");
      button.disabled = true; */




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



    this.arrays.push({poster: data.Poster, actors: data.Actors, director: data.Director, title:data.Title, country:data.Country, released: data.Released, genre: data.Genre, plot: data.Plot, imdb:data.imdbRating })


  }),

this.input=''
this.text=""

this.arrays.pop()

      }}}


</script>

<style scoped>

main{
   background-color:rgba(194, 176, 176, 0.548);

}

p{
  color:red
}

#demo{

  margin-top:60px;

}

#btn{
  border: 0px  ;
}
</style>
