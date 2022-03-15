<template>
 <div id="app">
   <main>
     <div class="search_box">
       <input type="text"
              class="search_bar"
              placeholder="Search..."
              v-model="query"
              @keypress="fetchWeather"
       >

     </div>

     <div class="weather-wrap">
       <div class="location-box">

         <div class="location">
           Saint Denis, FR
           <div class="date">
             Mardi 15 Mars 2022

           </div>
         </div>
       </div>

       <div class="weather-box">
         <div class="temp">
           9°C
           <div class="weather">
             Rain

           </div>
         </div>
       </div>
     </div>
   </main>
 </div>
</template>

<script>

export default {
  name: 'App',
  data (){
    return{
      api_key: '3e68242efc8b9ac84853efc8012c2eac',
      url_base: 'api.openweathermap.org/data/2.5/',
      query :'',
      weather: {}
    }
  },

  methods:{
    fetchWeather(e){
      if (e.key == "Enter"){
        fetch(`${this.api_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setResults);
      }
    }

  }

}
</script>
create a 2
<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  font-family: 'Quicksand';
}

#app{
  background-image: url("./assets/cold-bg.jpg");

  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

main{
  min-height: 100vh;
  padding: 25px;

  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75));
}

.search_box{
  width: 100%;
  margin-bottom: 30px;
}

.search_box .search_bar{
  display: block;
  width: 100%;
  padding: 15px;

  color: #313131;
  font-size: 20px;
  appearance: none;
  border: none;
  outline: none;
  background: none;

  box-shadow: 0 0 8px rgba(0,0,0,0.25);
  background-color: rgba(255,255,255,0.5);
  border-radius: 0px 16px 0px 16px;
  transition: 0.4s;
}

.search_box .search_bar:focus{
  box-shadow: 0 0 16px rgba(0,0,0,0.25);
  background-color: rgba(255,255,255,0.75);
  border-radius: 16px 0 16px 0;
}


.location-box .location{
  color: white;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0,0,0,0.25);
}

.location-box .date{
  color: white;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}

.weather-box{
  text-align: center;
}

.weather-box .temp{
  display: inline-block;
  padding: 10px 25px;
  color: white;
  font-size: 102px;
  font-weight: 900;

  text-shadow: 3px 6px rgba(0,0,0,0.25);
  background-color: rgba(255,255,255,0.25);
  border-radius: 16px;
  margin: 30px 0;

  box-shadow: 3px 6px rgba(0,0,0,0.25);
}

.weather-box .weather{
  color: white;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0,0,0,0.25);
}
</style>
