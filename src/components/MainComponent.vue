<template>
  <main>
    <select name="" id="" v-model="selezionato">
      <!--v-for di generi-->
      <option value="all">all</option>
      <option value="rock"></option>
    </select>
    {{selezionato}}
    <div class="container">
      <div class="songCard" v-for="(items, index) in songCards" :key="index">
        <div class="card">
          <img :src="items.poster" alt="" />
          <div class="card-text">
            <h4>{{ items.title }}</h4>
            <p>{{ items.author }}</p>
            <p>{{ items.year }}</p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "MainComponent",
  data() {
    return {
      songCards: {},
      selezionato:"",

      generi: {},
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        console.log(res.data);
        this.songCards = res.data.response;
        this.songCards.forEach((item)=>{
          console.log( "item" ,this.item)
          if(!this.songCards.includes(item.songCards)){
            this.songCards.push(item.songCards);
          }

        })

        //foreach di songCards
        //se il genere NON è contenuto nell'array this.genere allora =>
        //=>per ogni genere dentro una songCard inserisco tale genere nell'array this.generi
      })
      .catch((error) => {
        console.log(error);
      });
  },
  computed: {
    
  },
};
</script>

<style scoped>
main {
  background-color: hsl(209deg 33% 17%);
  height: calc(100vh - 60px);
}
.songCard {
  width: calc((100% / 5) - 20px);
  height: 290px;
  text-align: center;
  background-color: hsl(210deg 21% 23%);
  margin: 10px auto;
}
.card {
  display: flex;
  flex-flow: column;
  justify-content: center;
}
img {
  height: 160px;
  padding: 15px;
}
h4 {
  color: white;
  margin-bottom: 15px;
  padding: 0 5px;
}
p {
  color: hsl(217deg 4% 36%);
  font-size: 14px;
}
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  padding-top: 70px;
}
</style>
