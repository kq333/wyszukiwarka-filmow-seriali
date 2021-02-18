<template >

  <v-container>


<div id="demo"  >




<v-row >
   <v-col lg="10">


            <v-text-field ref="value"  clearable placeholder="Wpisz tytuł film/serialu" type="text" class="ml-4"  lg="4" xs="1"  v-model="input"></v-text-field>

    </v-col>

    <v-btn id="btn" outlined @click="klik" class="mt-4"  xs="1"><v-icon>search </v-icon></v-btn>

 </v-row>



  <v-row>
    <v-col >
      <div   v-for="arr in arrays" :key="arr.index" >
        <v-row>
          <v-col >
                <p  id="text1" >{{arr.title}}</p>
          </v-col>

                </v-row>

                  <v-row >
                    <v-col id="image"  lg="4" xs="1" >
                      <img  style="border-radius: 2%" class="ml-2" :src="arr.poster" />
                    </v-col>
                        <v-col  id="text" lg="7" xs="2" cols="6" class="ml-6">
                          <span  id="demo"> Aktorzy:</span> <span style=" font-size:1.5rem" class=" grey--text"> {{ arr.actors}}</span>
                          <p></p>

                          <span> Reżyseria:</span> <span>{{arr.director}}</span>
                          <p></p>
                          <span>Kraj: </span><span>{{arr.country}}</span>
                          <p></p>
                          <span>Rok produkcji: </span><span>{{arr.released}}</span>
                          <p></p>
                          <span>Gatunek: </span><span>{{arr.genre}}</span>
                          <p></p>
                          <span>Opis: </span><span>{{arr.plot}}</span>
                          <p></p>
                          <span>Ranking IMDB: </span><span>{{arr.imdb}}</span>
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

  klik(){

       this.input

       const inputValue = this.$refs.value.value

       if(inputValue>''){


    const url = 'https://www.omdbapi.com/?apikey=7bd5b2c8&t=';

    const result  = url + this.input;

    fetch(result)

  .then((res)=>{
      return res.json();
  })

  .then((data)=>{

    this.arrays.push({poster: data.Poster, actors: data.Actors, director: data.Director, title:data.Title, country:data.Country, released: data.Released, genre: data.Genre, plot: data.Plot, imdb:data.imdbRating

    })


  }),

this.input=''
/* this.text="" */

this.arrays.pop()

      }
      }
      }
      }


</script>

<style scoped>

#text1{
  display:flex;
  justify-content: center;
  align-items: center;
  font-size: 38px;
  color:rgba(128, 128, 128, 0.479);

}


#demo{

  margin-top:60px;

}



#btn{
  border: 0px  ;
}
</style>
